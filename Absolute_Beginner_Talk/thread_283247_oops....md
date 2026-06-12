---
title: "oops..."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-23
I just added an extra hard drive to my pc. They come up ok in the auto detect screen. However, when the xubuntu splash screen comes up, it is quickly replaced by a screen that says: "unable to mount" and then it has /dev/hda1 /proc /dev/hda and it dumps me into a shell. I obviously have lost the boot record or changed the location of linux but how do I get linux to look at the new configuration and adjust itself?](*,)

---

### Post by CatKiller on 2006-10-23
If the **only** change was putting in a new drive, and the old (Linux) drive was set up as Primary Master, keep it set up as Primary Master now.

---

### Post by DaveBorealis on 2006-10-23
> **saintj0n said:**
> replaced by a screen that says: "unable to mount" and then it has /dev/hda1 /proc /dev/hda and it dumps me into a shell.

Sounds like you might have placed your new hard drive where your old one was.  Perhpas when you plugged it in, your original hda became hdb, and the new became hda.

I've done that before, but it's been awhile and I think I solved it by making certain that my old was still master and the new was slave.

Hope this helps,
Dave

---

### Post by saintj0n on 2006-10-24
I don't remember how the drives were set up before. I didn't realize that linux made a distinction. With windoze, all I had to do was set up which drive would be bootable and I could select between win 98 or win XP. That's ok though. Id love to know how to fix it, but if I can't figure it out, I'll install win 98 on 1 partition and then ubuntu on the other and that should automatically set up in Grub. Right? (I hope)? I made sure there was nothing important on the pc just in case something spooky happened (I've seen linux do unexpected things before, ie: segmentation fault).

---

### Post by CatKiller on 2006-10-24
> **saintj0n said:**
> I don't remember how the drives were set up before. I didn't realize that linux made a distinction. 

Of course Linux makes a distinction - hda is not the same as hdb. It's just that with Windows, they can't both exist at the same time.

How are they set up now?

---

### Post by saintj0n on 2006-10-24
Currently, my situation is this:

HDA --- Windows 98 on a 15 Gb hard drive
HDC --- Ubuntu (Dapper) on a 15 Gb hard drive

when computer boots up, I get:

Loading Grub, please wait...
Error 17

I have no idea what went wrong. I had just done an oem install (it won't make it through an entire normal install, I tried three times) and it asked me to remove the CD and reboot. That is as far as I got....

](*,) :confused: :(

---

### Post by Drakkor on 2006-10-24
What I would do is "fixmbr" with windows disk,then reinstall grub with Ubuntu live disk,that may work ! :)

---

### Post by bulldog on 2006-10-24
Give us the output of ```
sudo fdisk -l
``` l as in like

So we can see your hdd configuration,with that knowledge we can instruct how to alter your GRUB.

And if possible give us your menu.lst too.

FYI 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by CatKiller on 2006-10-24
> **saintj0n said:**
> Currently, my situation is this:

HDA --- Windows 98 on a 15 Gb hard drive
HDC --- Ubuntu (Dapper) on a 15 Gb hard drive

when computer boots up, I get:

Loading Grub, please wait...
Error 17

I have no idea what went wrong. I had just done an oem install (it won't make it through an entire normal install, I tried three times) and it asked me to remove the CD and reboot. That is as far as I got....

](*,) :confused: :(

So not really "just added a hard drive" then?

You've moved the Linux drive to the wrong place, and possibly installed GRUB to the wrong drive. Depending on what else you've done, and what order you've done it in, moving the Linux drive to the Primary IDE channel **may** enable that drive to boot. You could then configure GRUB to boot the 98 disk by editing your menu.lst.

If it still won't boot after you've swapped the disks around, you're going to have to boot from a floppy to do a **fdisk /mbr** to get your 98 drive functional again, and install GRUB to the other drive, and then think about how you're going to set each of them up so that you can boot the other.

---

### Post by saintj0n on 2006-10-24
Originally, I had added a hard drive nad it did not work. So, I tried to simplify the problem by reinstalling  win 98. Once it was up and running, I installed ubuntu on the other drive using oem mode. I elected to use Grub. Btw, I don't know how to find menu.lst....

---

### Post by bukwirm on 2006-10-24
menu.lst is in /boot/grub

---

### Post by saintj0n on 2006-10-24
Ok..
I decided to reinstall ubuntu and worry about the win 98 later. I kept trying to install using oem mode but it said an installation step failed installing software(diveintopython). So, I decided to install a server and then add packages later. It went flawlessly. But now all that I have is a command line.:(  How do I make it so that it starts up in gnome(so I can start adding packages?

---

### Post by CatKiller on 2006-10-24
sudo apt-get install ubuntu-desktop

---

### Post by saintj0n on 2006-10-25
For now, I am going to just load windows 98 by changing the boot sequence in bios(I rarely use it). However, I assume there is a way to start the configuration process from inside Gnome..? It seems like the whole dual boot thing is alot harder than it should be....

---

### Post by Drakkor on 2006-10-25
To have permissions use ```
gksudo nautilus
``` then go to filesystem.boot,grub,menu.list

---

### Post by saintj0n on 2006-10-25
Which program can I use to set a bootable flag on a partition?

---

### Post by Drakkor on 2006-10-25
You can use the GParted live disk to set a bootable flag

---

