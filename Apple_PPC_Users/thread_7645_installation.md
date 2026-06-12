---
title: "installation"
date: 2004-12-09
forum: Apple PPC Users
---

### Post by h.ornstein on 2004-12-09
Hallo,

I have tried to install Ubuntu on my mac G4, on a second hdd, jumpered ad placed as master. At the end of the session the program restarts, I then get a message:

edit (1102606995.021:0): initialized
starting umbuntu
pivot-root: no such file or directory
/sbin/init:429 canot open dev/console: No such file
Kernel panic: Attempted to kill init

Where have I done something wrong?

Harald

---

### Post by rbran100 on 2004-12-09
Define "at the end of the session"  :  Does this mean that you get through the install "fine" and on reboot encounter an error?

---

### Post by rbran100 on 2004-12-09
Sorry as i am not a expert on mac installs at all:

[http://ubuntuforums.org/showthread.php?t=3995](http://ubuntuforums.org/showthread.php?t=3995)

This link may get you started till someone else more knowledgable comes along. [-X

---

### Post by h.ornstein on 2004-12-10
[QUOTE=rbran100]Define "at the end of the session"  :  Does this mean that you get through the install "fine" and on reboot encounter an error?[/QUOTE]
 The installation gave no problems,after the reboot comes a screen with text and then the quoted message.

Harald

---

### Post by Rohan on 2004-12-13
Yeah I get the same problem on a G4 400 Yikes...

---

### Post by jtucker on 2005-01-11
[QUOTE=h.ornstein]Hallo,

I have tried to install Ubuntu on my mac G4, on a second hdd, jumpered ad placed as master. At the end of the session the program restarts, I then get a message:

edit (1102606995.021:0): initialized
starting umbuntu
pivot-root: no such file or directory
/sbin/init:429 canot open dev/console: No such file
Kernel panic: Attempted to kill init

Where have I done something wrong?

Harald[/QUOTE]
Harald,

I had the same problem Ubuntu.  Had other kinds of problems with Debian and with YDL.  None would completely and successfully install on my B&W.

Two days of troubleshooting and I noticed some DMA errors in the Debian and YDL log (dmesg).  Searching those messages with Google finds lots of information pointing to IDE drive/cable/controller problems.  Usual suggestion was to disable DMA.

I eventually put my old SCSI card and drive in and Ubuntu is happily updating and configuring now.  I expect it to be successful.....oops, it finished as I was writing.  I'm now logged in to Ubuntu on my B&W with SCSI drive.  Mozilla up; so is OpenOffice.

Now to figure out how to fix the IDE problems........

---

