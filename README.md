xfr
===

Upload source files to a target device running [Mecrisp Forth](http://mecrisp.sourceforge.net/).
Tested with [picocom](https://github.com/npat-efault/picocom) terminal emulator.

Transmission synchronisation
----------------------------

After sending each line xfr waits for the Mecrisp Forth to respond with an
`ok.`. This allows successful transfer of files at high baud rates without
hardware flow control.

File inclusion
--------------

Sent file(s) may include other files.

<pre><code>
#include registers.forth
</code></pre>

Usage
-----

```sh
xfr [OPTIONS] INPUT-FILE
```

OPTIONS:

    -h, --help            show this help message and exit
    -c, --skip-comments   do not send comments
    -e, --skip-empty-lines
                          do not send empty lines
    -s, --print-statistics
                          print transfer statistics

Example
-------

```
picocom -b 1000000 /dev/ttyACM0 --imap lfcrlf,crcrlf --omap delbs,crlf --send-cmd "xfr -c -e -s"
```
