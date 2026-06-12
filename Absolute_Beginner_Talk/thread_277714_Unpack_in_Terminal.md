---
title: "Unpack in Terminal"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Unterseeboot_234 on 2006-10-15
Hello,

I wanted the API for OpenOffice. I go to the downloads at Sun. There are links for a Win zip or Linux. I chose the Linux, it downloads 37.8meg file. the only instructions for this file from a .pdf tutorial that my download is that:

file:///home/user/Desktop/so-sdk-8-pp3-bin-linux-en-US.sh

can be used as a build.

In Terminal mode, I can --->  
============================
[COLOR="Red"]user@computer1:~$ more filename[/COLOR]
and see...
============================

```
#!/bin/sh

linenum=88

UNPACKDIR=/var/tmp/unpack_staroffice
diskSpaceRequired=38750
checksum=22100

EXTRACTONLY="no"
if [ "$1" = "-x" ]
then
    EXTRACTONLY=yes
fi

# Determining current platform

platform=`uname -s`

case $platform in
SunOS)
  tail_prog="tail"
  ;;
Linux)
```
=========================================

if I type in Terminal [COLOR="Red"]user@computer1:~$ source filename[/COLOR]

I get up to the echo that asks for a file directory and then the Terminal quits. Nothing happens.
++++++++++++++++++++++++++++++++++++++++++

1. Is my file a shell script?
2. What command will "build"?

++++++++++++++++++++++++++++++++++++++++++

Thanks in advance, ubuntu people. I sure don't want to fire up Win to go get the zip. I want to do it the Linux version.

---

### Post by Sef on 2006-10-15
Check out [How to Install Anything.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Unterseeboot_234 on 2006-10-15
Hey thanks! ! ! The blog link is a useful resource I had no knowledge of. It's the ubuntu forums that bring back what computers were ... Personal Computer.

---

### Post by Sef on 2006-10-15
You're welcome.  I come back because of the forum of the friendliness and help from the people here.

---

