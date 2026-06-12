---
title: "udev &amp; modem stuff"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by navymom on 2006-07-24
I got my new hard drive...got my dual booting working....and now i'm working on my internet connect....i printed the wiki instructions for my modem configuration and everything goes fine until i have to create a text file with the following in it:

#ltmodem
KERNEL="ttyLTM0", SYMLINK="modem"

I have two problems with it...

1.  I have two folders with the name /etc/udev/rules.d/...one in the root and one in just the regular old file system...which one do i save it in?  file name should be 10-local.rules

2.  it won't let me save to either one of them.  it tells me i don't have permission to access that file/folder...help please?

Oh!  but everything else i've checked out so far is working beautifully.

Barbi

---

### Post by gargoyle on 2006-07-24
I am new to Ubuntu.
Are you editing in administrator mode.
**sudo gedit ltmodem**
Using sudo will give you permission to edit the file.

What instructions are you using? Could you post a link to the instruction page?

Good luck

---

### Post by navymom on 2006-07-24
i'm not trying to edit a file.  i'm trying to save one that the guide tells you in the wiki instructions.  it says to create a file and name it /etc/udev/rules.d/10-local.rules with those lines in the file.  when i try to save it, it tells me i don't have access....also, there are two folders called /etc/udev/rules.d....one in root and one in the files.


This is the instructions I'm using to install/configure my modem...my modem is a lucent winmodem.

[DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f")

---

