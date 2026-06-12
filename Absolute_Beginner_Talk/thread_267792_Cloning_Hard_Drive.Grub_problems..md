---
title: "Cloning Hard Drive.Grub problems."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by fishcake007 on 2006-09-29
This should be text book stuff , I've follow all the instructions.
I've just changed my laptops harddrive for a new bigger one , 
I booted from ubuntu live cd , stuck the old drive in an usb case and began the copy.First of all setting up the new disk with partions and swap using gparted and then dd to copy the stuff.
```

I dd bs=1M if=/dev/sda1 of=/dev/hda1. 

```
No problems what so ever , everything copied without any problems. 

I then edited the fstab and menu.1st , changing hdb1(the old drive) to hda1(the new drive). (The old laptop drive , had a jumper set to slave )

Ok now to reinstall grub
```

I did the following 
grub
>find  /boot/grub/stage1
 (hd0,0)
>root (hd0,0)
 Filesystem type is exr2fs, partition type 0x83
>setup (hd0)
 (This is the 2nd time I've run it.I want to install to MBR, I run no other OS)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exist... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)1+16 p /boot/grub/stage 2 /boot/grub/menu.1st.. succeeded
Done.

>quit

```

Reboot and nothing I get the following from bios

Searching for Boot Record from IDE-0.OK and then nothing.


I suspect that grub is at fault , I've edited fstab and menu.1st is there any other file I'm supposed to edit?
Anyone offer any help , I've been forced to borrow my girlfriends laptop to type this... and to make matter worse it's running XP.

---

### Post by indytim on 2006-09-29
If you're set up to burn an iso file, you might want to consider getting Super Grub and re-installing Grub from there. The link to the site is
[http://freshmeat.net/projects/supergrub/]("http://freshmeat.net/projects/supergrub/")

Hope this helps and good luck.

IndyTim

---

### Post by fishcake007 on 2006-09-29
Thanks, will give it a try tomorrow(no blank cdrs), I feel I wasted enough time on this one. I just can't see the problem , I thought I had it too , I forgot to make the drive bootable but changing this with cfdisk and reinstalling grub made no difference. I'm going to put all my faith in supergrub!

---

### Post by fishcake007 on 2006-09-30
Tried supergrub but it runs the same commands that I used , hence I have an unbootable system. I could boot the drive using the boot direct option from the supergrub cd which shows it works but why wont it boot normally?!:confused:  Not sure what to do! Damm Grub! Kill Grub!!! Aghhhhh](*,)

---

### Post by fishcake007 on 2006-10-03
Whoops.. found the problem ... forgot about editing /boot/grub/device.map , that'll teach me for not reading the faq/man page properly. I have to say am very impressed with dd for cloning a drive.

---

