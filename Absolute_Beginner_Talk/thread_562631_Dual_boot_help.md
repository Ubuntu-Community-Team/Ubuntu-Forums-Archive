---
title: "Dual boot help"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-09-29
Hey so I just went to boot my desktop and I got an error that i must reinstall some file

"<windows root>\system32\hal.dll"

Googling this I find that this can be a problem with the boot.ini which I believe Wubi may have modified.  I have just put in my other harddrive as the master so I can look at the boot and post it, but I was wondering if anyone knew how to help

---

### Post by axamax on 2007-09-29
You should be able to download a copy of hal.dll and copy it into windows, from a floppy, using DOS . It is quite a common fault

---

### Post by madmatrixz3000 on 2007-09-29
guide me through the steps if you can I have no desktop

---

### Post by madmatrixz3000 on 2007-09-29
Ahhhhhhhh how do I install the .dll file?

---

### Post by kellemes on 2007-09-29
Maybe this will help?
[http://support.microsoft.com/kb/330184]("http://support.microsoft.com/kb/330184")

---

### Post by madmatrixz3000 on 2007-09-29
Ok that gives me a guide, but how do I boot from the XP CD?

I go into the manual boot and select IDE CD Rom and it says 


"Press F1 to continue, F2 for setup"

I press F1 and it gives me the same prompt.  PLEASE HELP:confused:

---

### Post by louieb on 2007-09-29
Booting to a CD can sometime be a pain, Doesn't matter if its Window or Linux the step are the same.  Set you BIOS to make it look at the  CD drive first. Then reboot the the computer with the CD in the drive. Perhaps this will help [PuppyLinuxWiki: BootingFromCD]("http://puppylinux.org/wikka/BootingFromCD")

BTW: WUBI hasn't been around long enough for there to be a lot of people that can help you fix it when things go wrong.  But from reading their web site it does modify the boot.ini file.

---

