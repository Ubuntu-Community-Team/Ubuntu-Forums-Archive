---
title: "Install problems - Buffer I/O errors"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by vulcaan on 2007-01-31
Hi,

Trying to install ubuntu for the first time on my Dell Inspiron 9100, In the end Im looking to have setup a Windows XP and ubuntu dual boot. I have downloaded version 6.10 and 6.06 and also got a known working CD (from doing the install on a different PC), so thats 3 different CDs - all trying the Live CD option.

I first tried version 6.10 - when selecting the default option of startup and install, 

after the ubuntu spash screen I got the following error :

[17179764.296000] Buffer I/O error on device hdc, logical block X (Where X ranges from 0-9 while the error spams the display)

Seaching the forums I tried adding ide=noapic and ide=nolapic to the boot command, but it made no different, so I moved to version 6.06 :-

got alittle better with getting the following messages on/just after the spash screen :

Loading essential drivers - ok
Mounting root file system - ok
Uncompressing Linux... ok, booting the kernel.

[17179764.296000] Buffer I/O error on device hdc, logical block X (Where X ranges from 0-9 while the error spams the display)

again I tried added the extra commands I found from the forums but no joy, I also seen a post about trying puppylinux to check for hardware problems, puppylinux started up with no errors, but I would prefer to use ubuntu if I can get it installed.

Any advise is welcome,

---

### Post by vulcaan on 2007-02-01
No one have any suggestions ?

---

### Post by tiggerthump on 2007-02-08
Very similar problems here...

I get "Buffer I/O error on device dm-0"

Thinking my laptop hard drive life it over. Any advice would be most welcome. Particularly how to mount a network share when everything is read only. As I would like to attempt to move some files off the hard drive.

Oh, I also tried booting up the Ubuntu live CD. Annoyingly it could detect the hard drive partition but not mount it. Can't remember the exact error, but complaining it couldn't get the superblock size (i think).

Bugger, knew I should have setup that rsync backup-ing!

---

