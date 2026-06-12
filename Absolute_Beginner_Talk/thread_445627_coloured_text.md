---
title: "coloured text"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by richard101 on 2007-05-16
Hi All

sorry for dumb question - but cannot google answer.

Whats does the different coloured text signify when you make a directory listing?
(in ubuntu 6.06)

also, re text. I want <a small-case letter L> to be a shortcut for "ls -lt".

(Somehow I did this once before in solaris by putting an alias in .profile - I think)


thanks

richard101

---

### Post by Madpilot on 2007-05-16
Blue text is directories.

I'm actually not sure what green & purple signifiy, and neither "man ls" nor "info ls" were helpful...

---

### Post by Najand on 2007-05-16
For alias put the following in ".bashrc" file:
```

alias l = "ls -lt"

```

---

### Post by Najand on 2007-05-16
The default colors are:
> * Executable files: Green
* Normal file : Normal
* Directory: Blue
* Symbolic link : Cyan
* Pipe: Yellow
* Socket: Magenta
* Block device driver: Bold yellow foreground, with black background
* Character device driver: Bold yellow foreground, with black background
* Orphaned syminks : Blinking Bold white with red background
* Missing links ( - and the files they point to) : Blinking Bold white with red background
* Archives or compressed : Red (.tar, .gz, .zip, .rpm)
* Image files : Magenta (.jpg, gif, bmp, png, tif)

---

### Post by richard101 on 2007-05-16
Thanks all, perfect.

---

