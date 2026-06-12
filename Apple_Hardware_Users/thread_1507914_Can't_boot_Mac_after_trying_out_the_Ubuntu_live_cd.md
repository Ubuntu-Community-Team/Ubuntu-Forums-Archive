---
title: "Can't boot Mac after trying out the Ubuntu live cd!"
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by Tommerz on 2010-06-12
Hello,

I have a serious problem! I downloaded and burnt Ubuntu 10.04 and then chose it as start up volume in Snow Leopard's start up disk preference dialogue and although Ubuntu runs successfully from the cd (I'm typing from it now) I can no longer boot into OS X at all.

I have tried all of the different short cuts at boot up to no avail, even trying 2 keyboards. It insists on looking for the Ubuntu disk and if it is not in the drive comes up with an error message stating that a system disk cannot be found.

Is there any kind of tool on Ubuntu that will let me change the start up disc/interact with the Mac's efi settings? I previously had refit installed but this disappeared just before I booted the cd, is it worth using the live cd? 

I tried booting from a Tiger dvd but it wouldn't let me do so, it just returned me to the ominous "System disk not found" message.

Does anyone have any kind of idea? Perhaps some kind of shell script that will reinstall refit? I'm guessing that any kind of dvd designed for PC will prob boot, any kind of OS X recovery disk compatible with MBR available?

Thanks :confused:

---

### Post by radddi on 2010-06-12
Since the Ubuntu LiveCD itself never changes anything in the system, especially the boot options, I suppose your problem lies with your settings. You said that you changed the start up disk from within Snow Leopard, the OS. You could try to access your computer's boot menu and see if the primary boot device is set so the CD/DVD rather than the first hard disc. I found the following threads on the net which might help:

[http://forums.macnn.com/69/mac-notebooks/350824/mac-boot-menu-system-setup/](http://forums.macnn.com/69/mac-notebooks/350824/mac-boot-menu-system-setup/)
[http://www.macworld.com/article/145996/2010/01/bootmenu.html](http://www.macworld.com/article/145996/2010/01/bootmenu.html)

> the boot manager&#8212;this is the screen that shows the bootable drives on startup (or reboot). You can make this screen appear by holding down the Option key during startup, which is the typically-prescribed method

Best of luck to you. :)

---

### Post by Tommerz on 2010-06-12
Thanks Radddi, the first link relates to Powerpc Macs. Apparently there is a bug in 10.04 which means it affects the Mac's boot loader even if only loaded as a live cd... strange.

The second link is very useful, I'm going to try it now (I'm concerned in case the problem lies with my keyboard). I will repost here when I've attempted it.

):P bye for now

---

### Post by Tommerz on 2010-06-12
Hey, to my surprise it worked (!) must have been something to do with my keyboard(s).

Thank you so much for your help, I actually think the using a remote to boot method should be stickied somewhere as it worked whereas two keyboards didn't - might help quite a few people out!

:guitar:

---

### Post by radddi on 2010-06-13
I'm glad I could help. Have a splendid day. :popcorn:

---

### Post by Colonel Dragoon on 2010-06-14
even though this problm has been solved, I personally suggest installing rEFit on mac, as it offers boot options to different OSs; just in case to prevent further or future complications.

---

### Post by Colonel Dragoon on 2010-06-14
even though this problem has been solved, I personally suggest installing rEFit on mac OSX, as it offers boot options to different OSs; just in case to prevent further or future complications.

---

### Post by spacepad on 2010-06-20
I ran into something very similar today after erasing my HD (which had Mac + Ubuntu) and restoring from back-up.  Mac OS would not load and I just had the black screen error message stating that a system disk cannot be found and please insert the CD.  Zapping the PRAM fixed it.
> **Resetting PRAM and NVRAM**
[LIST=1]
[*]Shut down the computer.
[*]Locate the following keys on the keyboard: Command, Option, P, and R. You will need to hold these keys down simultaneously in step 4.
[*]Turn on the computer.
[*]Press and hold the Command-Option-P-R keys. You must press this key combination before the gray screen appears.
[*]Hold the keys down until the computer restarts and you hear the startup sound for the second time.
[*]Release the keys.
[/LIST]
Your computer's PRAM and the NVRAM are reset to the default values. The clock settings may be reset to a default date on some models.[http://support.apple.com/kb/ht1379](http://support.apple.com/kb/ht1379)

---

