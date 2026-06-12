---
title: "Ubuntu from USB"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by nobbi on 2006-06-29
Hello there, hope you've got a minute for a little noob : )

I got this little Subnotebook here with a pre-installed Ubuntu (it's dutch! wth...?)
Well, i always wanted to try Ubuntu, and this is just the right moment I guess.

Problem: It's locked up, so I can't use it (you know, passwords and such)
So, the noob here thinks of: Format and install it on your own.
Problems faced now are:
 1) I don't know how to get somewhere to make it wipe it's HD
 2) This buddy got no CD or Floppy, just an USB-Port, and since I can't get into Bios I don't know how to make it boot from there :/

 I'm sorry for asking possibly stupid things, but I did not find anything yet :/

---

### Post by n00b@linux on 2006-06-29
Hmmm. How did you come to possess such an item?

---

### Post by nobbi on 2006-06-29
well, such strange items are mostly acquired through the evil and twisted basars of ebay - though this information does not give any help to this problem i guess ^^

btw: It's a Toshiba Portege 7010CT, for all those who're curious

---

### Post by x64Jimbo on 2006-06-29
The BIOS is pretty much your only recourse. Search around the internet for a manual for that model and you should be able to find how. The most common key to enter the BIOS setup on Toshibas is the ESC key. Try tapping ESC repeatedly right after you power it on.

---

### Post by TestUser on 2006-06-29
Hi

I placed laptop HDD in stationary PC and installed ubuntu, unfortunately I got into HW problems. But with a working grub I just placed linux.bin and
initrd.gz in boot and then edited /boot/grub/menu.lst and added 
title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz

All described here:
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)
Since I had a working grub I did not exactly follow this ...

You can try to DL the 2 files from dapper, but if you have problems use hoary and do a dist upgrade.
Read the info in the link and if you get into problems me or someone else guide you.

TU

---

### Post by nobbi on 2006-06-29
thanks so far : )

the key to enter bios was <esc> ... well, i only tried <F1> and <DEL> - my fault for sure ^^

but still i'm stuck:
the bios has no tag for USB-booting, only
HDD
FDD (which it doesn't have)
LAN (which it doesn't have)
and
CD-ROM (which it doesn't have)

yay

I also tried to check on the HDD to put into a USB-Case, but the notebookHD has much smaller contact-spacing.

I'm going to try to reconfigure the GRUB on this one, maybe it could start something from the USB-port... hope I'll find some manual and won't screw up at this, never done it before ^^
 - well... if i can get into grub, that is...

---

### Post by olsonar on 2006-06-29
i've heard there's a way to boot the installer from a 1GB+ USB stick, so that's an option if you have one.

EDIT: [https://wiki.ubuntu.com/Installation/FromUSBStick](https://wiki.ubuntu.com/Installation/FromUSBStick)

---

### Post by nobbi on 2006-06-30
i thought of this one...
but as i said before, the bios has no tag to boot from USB

i feel kinda lost, my head's all wobbly now ~_~

---

### Post by TestUser on 2006-07-01
Hi

Try the way I told you. 

Since you have a working ubuntu installation but no PW to login. Remove HDD and place in other laptop with CD or stationary PC with an adapter from 3.5"-2.5" HDD, it costs something like 5 USD.  
When you can read the HDD you just place the 2 files mentioned in link in boot and then edit menu.lst and add the 3 lines from same link.

I do not know if it is possible to reset PW so better to do a reinstall.

TU

---

