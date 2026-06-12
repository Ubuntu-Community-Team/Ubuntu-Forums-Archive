---
title: "GFX GRUB first time user"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Ebtoulson on 2008-01-20
Alright well I'm a first time user of linux and wanted to dual boot ubuntu on my vista laptop. I read some articles about grub, and gfx grub (basically grub with eye candy) and I wanted to know if I could install GFX GRUB in windows or if I have to install it in ubuntu. 

Another question is, is there a way to make/get a boot loader to automatically boot from a certain OS unless I tell it other wise (kind of like having a timer that if I don't press anything in 10 sec it will just boot up windows) because I'm still going to use windows until I get comfortable with ubuntu.

---

### Post by A4006 on 2008-01-20
I've never used GFX GRUB, but I imagine it would have to be installed from Ubuntu, seeing as GRUB is for the most part only modifiable from Linux.  Also, you can change the order of the OS's shown in the GRUB menu using this article <https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS>.  You could also try a program called EasyBCD, which is a program for Vista that allows you to modify the Vista MBR to boot different operating systems, although you'll probably have to reset your MBR to windows from GRUB using the Vista repair CD (type "bootrec.exe" in the repair CD's command prompt for a list of commands).  <http://apcmag.com/5045/how_to_dual_boot_vista_with_linux> shows you how to reset GRUB as the default boot loader, in case you screw it up (happens to me a lot)

---

### Post by chewearn on 2008-01-20
As a first time linux user, I would strongly advise you against messing with grub and gfxboot until you are comfortable with linux command line and fixing grub/boot-up problems.

Currently, gfxboot is not "supported natively" by ubuntu; that is, you can't just make it work with a few button clicks.  You need to edit /boot/grub/menu.lst; you need to remove grub and replace it by gfxboot.  And since gfxboot is not in the ubuntu repositories, you need to manually download the deb file, install and configure; etc.

If you really really want to play around, and don't mind breaking things, then here is the thread for gfxboot:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

If you break it, you pay for it.

---

### Post by Ebtoulson on 2008-01-20
Thank for the quick replies. Yea after looking at the gfx command lines I don't think Im ready for that. Instead I'm probably just going to stick with GRUB and change the order with (the following link)

> **A4006 said:**
> <https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS>.  
For some reason whenever this link is posted it puts a space before the "e" in space.

As mentioned GFX isn't natively compatible "yet" so I'll think I'll just wait till it is. 

And as far as breaking my pc, dont think I'll be trying that either at least not on my new laptop (maybe on a spare old pc). 
> **AstalaVista said:**
> If you really really want to play around, and don't mind breaking things, then here is the thread for gfxboot:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

If you break it, you pay for it.

Really thanks for your help..actually one reason I'm trying Ubuntu (posted 1 hr after I did)

---

