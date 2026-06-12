---
title: "Yaboot.conf is hosed.  Anyone know how to manually call a kernel?"
date: 2007-10-26
forum: Apple PPC Users
---

### Post by magnolia fan on 2007-10-26
Hi, just successfully upgraded to Gutsy, but then later I broke my yaboot.conf file.  Computer won't boot into linux now.  Anyone know exactly what to type on the boot screen to manually select a kernel?  I know I'm on partition 12, and the kernal is in /boot/.   Can't get it to select the vmlinux though.

I'm typing "hd:12,/boot/vmlinux" following the "boot:" prompt.  But it doesn't work.

--thanks

---

### Post by Alex Carter on 2007-10-26
You need to specify the OpenFirmware adress of your hd after the boot prompt. If you enter 'help' or something at the yaboot prompt, it will give you instructions, and among them there should be a line representing this OF address I mentioned. That's the long one, with the at-signs and all that stuff. Then copy the address, after the colon insert your partition number (12 in your case) and then the rest stuff, /boot/ etc.

---

### Post by Alex Carter on 2007-10-26
[http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)

This can be useful for you, if above won't work. Or you can just boot from LiveCD to fix the broken yaboot.conf.

---

### Post by magnolia fan on 2007-10-26
I tried the very long entry you suggested on the boot screen for my device and partition with all the "@" symbols and that got things going with lines rolling down the screen, but then it ended with a kernel panic.

This is roughly what the boot screen then displayed in the last 4 lines following the attempt to boot:

Line 1:
VFS: Cannot open root device "<null>" or unknown block (8,1)
Line 2:
Please append correct "root" boot option
Line 3:
kernel panic - not syncing: VFS: unable to mount root fs on unknown block (8,1)
Line 4:
Rebooting in 180 seconds



Thanks for the previous advice, let me know if you have any further suggestions.

---

### Post by magnolia fan on 2007-10-26
The only other thing I can think of is that I might change the /boot/vmlinux line that I'm entereing to /boot/vmlinux-2.6.2????  whatever it is for the PPC install.  My current vmlinux is pointing to an older kernel because the Gutsy upgrade didn't update it.  

Does anyone know the exact name of the Gutsy vmlinux-2.6.whatever file in /boot/   ???

---

### Post by Alex Carter on 2007-10-27
2.6.22-14-powerpc is the name.
But vmlinux is the soft symlink to the vmlinux-2.6.xxx file, then even if Gutsy did not update this symlink, it should point to the old vmlinux file which worked fine for you. 
So I suppose that it is not the problem, but you should try.

---

### Post by Alex Carter on 2007-10-27
Actually, there is a 100% working method to boot your machine into linux. If you're dual booting, that you could download initrd and linux images, store it to your hard drive, HFS partition and boot from them using openfirmware boot options. I could explain it better, if you suggest you should try. 
Another option is to boot from livecd of ubuntu (if you have downloaded one), then mount your linux partition and change yaboot.conf file. Then update yaboot, reboot and you should be fine. 
Please write which method you want to try and I will provide you more detailed instructions.
Second method is much easier.

---

### Post by Alex Carter on 2007-10-27
Oh, one more thing.
Maybe I was not too clear and misguided you some way... 
The openfirmware address of an hdd should be printed out like this: 
w/@00d04b4a1905397c/sbp-2@c000/disk@0:
(yours will differ, of course, but formatting will be the same). Then you enter 12 after the colon and the rest stuff.

---

### Post by stmiller on 2007-10-27
Another method is to boot the PowerPC Alternative CD, press TAB at the boot menu and choose 'rescue mode.'

In that rescue mode there is an option to repair yaboot. Done. :)

---

### Post by magnolia fan on 2007-10-30
I downloaded the Gutsy 7.10 Alternate CD for PPC, but the Re-install Yaboot.conf returns an error: "Rescue Operation Failed with Exit Code 255". 

I'll probably just re-install the entire thing.  Aside from some configuration issues in email, I haven't used it for much anyway. 

--thanks for the help.

---

