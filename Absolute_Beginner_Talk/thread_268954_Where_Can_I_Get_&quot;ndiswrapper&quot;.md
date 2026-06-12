---
title: "Where Can I Get &quot;ndiswrapper&quot;?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-09-30
Hi, where can I get ndiswrapper? And, how will I get it onto my computer (the one with Linux on it) from the one I'm on? (because my computer with Linux currently doesn't have internet).

---

### Post by pay on 2006-10-01
A simple google search found it, maybe you should try that first.
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
to get it on the other computer you can burn it to a disc or put it on a usb disc.

---

### Post by sbergman27 on 2006-10-01
Do you know what wireless chipset you have.  There is a super simple way to install this if it is a broadcom 43xx, which I do not believe requires any network connection.

You'll need to burn a script to CD or move it via floppy or something.

Here is compwiz's excellent script for the popular broadcom 43xx:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+compwiz](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+compwiz)

---

### Post by aysiu on 2006-10-01
I believe it's on both the Desktop CD and the Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

