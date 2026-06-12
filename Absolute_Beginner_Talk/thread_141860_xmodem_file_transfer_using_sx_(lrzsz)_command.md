---
title: "xmodem file transfer using sx (lrzsz) command"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by rogera on 2006-03-09
I wish to send a file to a remote computer using the xmodem/zmodem protocol through serial device /dev/ttyS0. I have installed the lrzsz package which has a number of commands, one of which is the sx command used to send a file using the xmodem protocol. I have read the man pages, but I cannot see where it says where the file is sent, or how to configure where it is sent.

Has anybody any examples of how to use the sx/sz command?

---

### Post by larytet on 2008-03-31
i think that minicom should do the trick
make sure that in the minicom setup /usr/bin/rx and /usr/bin/sx are specified
sud apt-get install minicom
run minicom 
Use Ctrl-A followed by  Z to enter minicom menu
menu configure minicom, serial port configuration
Call in/Call out programs

hope i helped

---

