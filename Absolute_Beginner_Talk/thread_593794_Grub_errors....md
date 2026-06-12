---
title: "Grub errors..."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-27
I just reinstalled Gusty, and I'm getting some Grub errors.  The first is when I try booting Ubuntu, I get a Grub error 17.  The first time I tried booting after reinstalling, I got this error, and changed the line 'hd(1,0)' to 'hd(0,0)', and I was able to boot.  Now it's still 'hd(0,0)', but I can't boot.  

Grub is installed on an external hard drive.  I think that I might have accidentally also installed it on the internal one, because when I unplug the external hard drive, Grub starts to load, and then it gives me a stage 1.5 error 21.  If I did install it on my Windows MBR, what are the two commands you run from the Windows recovery disk to restore the Windows MBR?

If I did overwrite the Windows MBR, would that be why I get a Grub error 13 when I try booting it, or is that something else?

Thanks.

---

### Post by Yes on 2007-10-27
I have no idea why, but I just reinstalled Grub, and now if I change 'hd(0,0)' to 'hd(1,0)', I can boot into Ubuntu.  I still get the errors when I try to boot Windows, though.

---

### Post by disturbedite on 2007-10-27
i had the SAME EXACT problem when i did a fresh install of gutsy.  i told it to use an entire drive to install on but grub did not know the correct location of the MBR.  it was set to hd(1,0) instead of hd(0,0) as it should have been.

this seems like a stupid mistake that should have been corrected before gutsy was released, considering it prevents one from booting the OS....
but it may have been the fact that i used the guided install instead of the manual one.

btw, just in case anyone doesn't know, you have to "fix" this problem by editing the /boot/grub/menu.lst as su/root and save it so that you don't have to edit the grub command line each time you boot or reboot.

---

### Post by Yes on 2007-10-27
I booted from the Windows recovery disk and ran fixmbr, and now everything's fine.  Thanks!

---

### Post by Maestro23 on 2007-10-27
> **Yes said:**
> I booted from the Windows recovery disk and ran fixmbr, and now everything's fine.  Thanks!

Good deal man.  Can you mark this SOLVED using the Thread Tools.
Thanks.:)

---

### Post by fsufitch on 2007-10-28
Yo. I managed to convince one of my friends to give Linux a shot (victoryyy:):)) but I've been having issues with the install. Everything installs smoothly, but there's a problem with booting. Grub always returns Stage 1.5 Error 21. I really wish its errors could be a bit more descriptive...
So, here's what I tried to do. I live-boot from the CD and go in and change /boot/grub/menu.lst. The system is supposed to dual-boot XP and Ubuntu, and they're each on a different HD. I think there may be another purely-data HD involved, but I'm not sure. Anyway, the point is that in device.map, hd0 and hd1 are registered. I tried all combos for the setting of root for the boot settings in menu.lst. No go.
Am I the only one having multiple-HD problems? I can't test it on my laptop, as here I just have 1 hard drive, 3 partitions. ^_^
Is there a quick solution? I've already been through 2 Ubuntu releases and been unsuccessful installing it...

---

### Post by meierfra on 2007-10-28
Does the grub menu show up at boot up? 
If not, you need to reinstall grub:[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

If this did not help, post  your "menu.lst" and the output  of "sudo fdisk -l".

---

### Post by strabes on 2007-10-28
See the GRUB link in my signature. meierfra you need to fix the url in your post.

---

### Post by meierfra on 2007-10-28
> meierfra you need to fix the url in your post.  	


Done. Thanks.

---

### Post by fsufitch on 2007-10-28
No, the grub menu doesn't show up. I can't get the info you asked, as the computer that I'm talking about is about 20 km away. I'll get them to run the stuff though ASAP. You're asking me to run it from the Live CD boot, right?

And fyi, grub is dead atm. I had to leave the computer in a usable state, so I had to run fixmbr.

---

### Post by meierfra on 2007-10-28
> You're asking me to run it from the Live CD boot, right? 
Yes, (To get  to the menu.lst  you will need to mount your ubuntu partition in the Live CD. Let  us  know if you need help with that.)


> And fyi, grub is dead atm. I had to leave the computer in a usable state, so I had to run fixmbr.

No problem, You needed to reinstall grub anyway.

---

