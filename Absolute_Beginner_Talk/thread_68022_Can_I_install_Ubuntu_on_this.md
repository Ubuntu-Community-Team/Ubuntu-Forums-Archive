---
title: "Can I install Ubuntu on this?"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by josebalius on 2005-09-21
Hi guys, and sorry for being such a...."newbie"

But can I install Ubuntu on something like this:

[http://www.wdc.com/en/products/Products.asp?DriveID=108](http://www.wdc.com/en/products/Products.asp?DriveID=108)

I am willing to buy it, I really do not want to touch the hard-drive and mess up my current stuff, So I was wondering if buying that would solve my problem?

Thank you,

Jose.

---

### Post by holiday on 2005-09-21
[QUOTE=josebalius]Hi guys, and sorry for being such a...."newbie"

But can I install Ubuntu on something like this:

[http://www.wdc.com/en/products/Products.asp?DriveID=108](http://www.wdc.com/en/products/Products.asp?DriveID=108)

I am willing to buy it, I really do not want to touch the hard-drive and mess up my current stuff, So I was wondering if buying that would solve my problem?

Thank you,

Jose.[/QUOTE]
 It depends on your base machine - the one you'll connect this drive to. If its BIOS supports booting from a USB device then you've made step 1. 

Step 2 is to check the wiki on HardwareCompatibility for ubuntu
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) If your drive is there then you're probably ok. If it's not then consider one of the drives that *is* there. 

You'll have to poke around just a little bit to find the list, but it's there. 

Good luck.

---

### Post by josebalius on 2005-09-21
[QUOTE=holiday]It depends on your base machine - the one you'll connect this drive to. If its BIOS supports booting from a USB device then you've made step 1. 

Step 2 is to check the wiki on HardwareCompatibility for ubuntu
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) If your drive is there then you're probably ok. If it's not then consider one of the drives that *is* there. 

You'll have to poke around just a little bit to find the list, but it's there. 

Good luck.[/QUOTE]
 Thank you :)

If you wouldn't mind answering, any idea how to know if my BIOS support booting from a usb device? I have an HP (if that matters lol).

Edit: I found this: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) but that is the best I have gotten, I'm I in right path? lol

Thank you

---

### Post by holiday on 2005-09-21
[QUOTE=josebalius]Thank you :)

If you wouldn't mind answering, any idea how to know if my BIOS support booting from a usb device? I have an HP (if that matters lol).

Edit: I found this: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) but that is the best I have gotten, I'm I in right path? lol

Thank you[/QUOTE]
 I don't know about the HP, but if you look closely at the bootup screen, you will probably see in some obscure part of the screen a tiny piece of script saying something like 'choose boot device' or 'boot options'.

You *could* try putting your model number into the HP site. No guarantee there, but ...

I think the best bet is to look closely at the screen when your computer first starts up. 

You'll get a menu that will list the devices that you can choose to boot from. If anything looks like an external drive then give it a chance. Go buy somewhere (a compatible drive) and if it doesn't work just take it back and demand your money back. 

It's worth the struggle. It really is. Hang in there.

---

### Post by josebalius on 2005-09-21
[QUOTE=holiday]I don't know about the HP, but if you look closely at the bootup screen, you will probably see in some obscure part of the screen a tiny piece of script saying something like 'choose boot device' or 'boot options'.

You *could* try putting your model number into the HP site. No guarantee there, but ...

I think the best bet is to look closely at the screen when your computer first starts up. 

You'll get a menu that will list the devices that you can choose to boot from. If anything looks like an external drive then give it a chance. Go buy somewhere (a compatible drive) and if it doesn't work just take it back and demand your money back. 

It's worth the struggle. It really is. Hang in there.[/QUOTE]
 Thanks,

So far I'm loving Ubuntu....and my computer uses the Live CD at an incredible speed (the same speed it runs windows), so if there was a way to keep the work that I do while running on the CD, I would be a made man but unfortunately there isn't :(

Thanks, I'll keep searching.

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=josebalius]Thanks,

So far I'm loving Ubuntu....and my computer uses the Live CD at an incredible speed (the same speed it runs windows), so if there was a way to keep the work that I do while running on the CD, I would be a made man but unfortunately there isn't :(

Thanks, I'll keep searching.[/QUOTE]
If you have a cheap USB pendrive/flashdrive, you can run the LiveCD, and mount the flash drive and save your data there.  You'd still be booting off the CD-ROM, but you'd have a little permanent storage space.

---

### Post by josebalius on 2005-09-21
[QUOTE=cwaldbieser]If you have a cheap USB pendrive/flashdrive, you can run the LiveCD, and mount the flash drive and save your data there.  You'd still be booting off the CD-ROM, but you'd have a little permanent storage space.[/QUOTE]
 ooooh, never thought about that. That would be much easier........

When you mean mount? Is it just plugin it in? or is there something I have to do?

Thanks for all the help guys.

---

### Post by josebalius on 2005-09-21
[QUOTE=josebalius]ooooh, never thought about that. That would be much easier........

When you mean mount? Is it just plugin it in? or is there something I have to do?

Thanks for all the help guys.[/QUOTE]
 I'm really sorry for the second post, if I buy an external hard-drive (kinda need one anyways) will I be able to use it just like how I would use a USB Flashdrive/pendrive?

---

### Post by erikpiper on 2005-09-21
[QUOTE=josebalius]I'm really sorry for the second post, if I buy an external hard-drive (kinda need one anyways) will I be able to use it just like how I would use a USB Flashdrive/pendrive?[/QUOTE]
 You should be able to...

Seriously, how big is your internal HD? I have a 30Gig HD on my laptop, and I dualboot. Plenty of room.Ubuntu from the internal HD is SOOOOO much faster!!! And to choose between linux and windows you just need to use the arrow keys, and the enter key! :) 

Dual booting will not dissapoint you :)  Just be cautious, and it will be fine.

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=josebalius]ooooh, never thought about that. That would be much easier........

When you mean mount? Is it just plugin it in? or is there something I have to do?

Thanks for all the help guys.[/QUOTE]
Mounting is jargon that means taking a storage device and adding it to your filesystem.  In Unix, the filesystem appears basically uniform from a user perspective, but it could be made up of many different drives, partitions, etc.

When you plug in your USB device, it should be mounted automatically for you.  There is a program that runs in the background called "gnome-volume-manager" that does this for you.  You can always mount a drive manually with the "mount" command, too.  The basic syntax is:

```
$ sudo mount -t filesystem-type device-file mount-point
``` 
filesystem-type could be "ext3", "ext2", "reiserfs", "fat", "ntfs", etc.
device-file is something like /dev/hda1, /dev/sdb1, /dev/fd0, or /dev/cdrom.
mount-point is just an empty folder which will serve as the "top" of the filesystem you are adding.  the gnome-volume-manager always mounts everything under /media.  You can mount filesystems anywhere you want though.  A typical place is in /mnt.

The opposite command is "umount" to unmount a filesystem.

---

### Post by josebalius on 2005-09-22
[QUOTE=erikpiper]You should be able to...

Seriously, how big is your internal HD? I have a 30Gig HD on my laptop, and I dualboot. Plenty of room.Ubuntu from the internal HD is SOOOOO much faster!!! And to choose between linux and windows you just need to use the arrow keys, and the enter key! :) 

Dual booting will not dissapoint you :)  Just be cautious, and it will be fine.[/QUOTE]

Hi,

My HD is about 186 GB. Heck I even did a parititon and separated 10GB for Ubuntu. My fear is while doing the installation is it a complete SURE that I'll be able to select on which parition I want to put it in?

---

