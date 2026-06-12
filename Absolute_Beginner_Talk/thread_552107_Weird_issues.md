---
title: "Weird issues"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by jflkbob on 2007-09-16
This is the second time I have tried to install Ubuntu on my computer.  The first time I tried, the installer would crash when trying to install grub.  I finally got it to work, and Ubuntu booted fine. I decided to check on windows, and it wouldn't load. Odd...  I went back to Ubuntu and I couldn't see my windows partition.  What?!  I assumed this was related to the non-booting of windows, so I booted via floppies to a partition viewer.  It turns out that my windows partition had been reduced to 30 mb!  :shock:  I assume this is from the installer crashing, but I am not sure.:(  Even worse, I had forgotten to back up my files, so that really sucked.:cry:


Anyway... to the current problem. I have tried again (this time backing up:)) and the installation went well.  I rebooted and found that Ubuntu wouldn't boot. I freaked and tried windows, to find that it didn't boot. I checked partitions and found that both were safe and sound. I tried Ubuntu again, and found that it worked. Curious, I tried windows. Nothing. I tried to go back to Ubuntu and it wouldn't boot. After a few hours of frustration, I tried to boot off of an old hard drive.  No success. I removed both hard drives, and tried just the old one.  Nothing.  I put my current drive back in to find Ubuntu works! I am typing this from Ubuntu.

Does anyone have any idea what I should do to get windows working?

Odd little thing I encountered, I tried to use sudo fdisk -1 because I have read to do that in posts about similar issues

It asked me for my password, which I entered then nothing happened.
I tried it again, but this time it doesn't even ask for a password! 
WHAT THE HECK IS WRONG WITH MY SYSTEM?!:confused:

---

### Post by Crafty Kisses on 2007-09-16
Not sure if this helps, but the username and password are case-sensitive.

---

### Post by jflkbob on 2007-09-16
The password is numerical, so it can't be case sensitive.  I hope.8-[

---

### Post by jflkbob on 2007-09-16
I tried restarting the computer for reasons unknown and guess what? Ubuntu won't load!
I realized that it worked after a hardware change, so I removed my floppy trying to get it to work.
Nothing, so I plugged it back in and it worked.

Really weird, I just thought you guys should know.

---

### Post by ravenwere on 2007-09-16
Need more information.

You will need to post the output of ```
sudo fdisk -l
``` and also post a copy of your /boot/grub/menu.lst file.

Are you saying the Grub menu is appearing OK?

When you install/reinstall the drives (are they IDE or SATA) Did you edit the GRUB menu.list file accordingly? My understanding is the Grub points to a bootable partition Linux or Windows. Changing the hardware configuration will mean Grub may point to the wrong partition.

For an idea see [http://ubuntuforums.org/showthread.php?p=1319395](http://ubuntuforums.org/showthread.php?p=1319395)

Also for future installations I would recommend you manually partition your drive and use a separate partition for your /home file then you can reinstall protecting your files as long as you don't reformat that partition. see [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
for ideas.

---

### Post by jflkbob on 2007-09-16
The output of sudo fdisk -l
```
will@william-desktop:~$ sudo fdisk -l
will@william-desktop:~$ 

```

Why does it torment me so?

The Grub menu functions just fine, its just that the OS's don't always boot.
Grub menu:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d35cc34b-4fa8-4cad-99c6-d4c2cbff1fcf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d35cc34b-4fa8-4cad-99c6-d4c2cbff1fcf ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

My current hard drive is SATA and the one I tried to boot off of was IDE.

> Changing the hardware configuration will mean Grub may point to the wrong partition.


Windows failed to load prior to the hardware change.

---

### Post by jflkbob on 2007-09-16
Thank-you anyone who tried to help me, but I am going to format and forget Ubuntu.

Goodbye and again, thank-you.

---

### Post by ravenwere on 2007-09-16
For the information of future followers of this thread:

The fact that fdisk -l returned nothing may indicate that for whatever reason the disk is not being detected. This could be a hardware fault.

The next step I would have taken was to boot in recovery mode and check how far the boot process was successful.

---

### Post by JBAlaska on 2007-09-16
Probably a quick run of the repair console in XP would have fixed to XP boot issue. It's a shame some ppl are so impatient and quick to format.  oh well.

---

