---
title: "Installed FreeBSD dual boot - Ubuntu won't boot now!"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by eric.stone on 2006-01-30
Tried to dual boot FreeBSD and my beloved ubuntu.  Loaded the FreeBSD boot loader.  Linux is offered as a choice, but nothing happens when I select linux.  Any suggestions for getting ubuntu back? Can I restore grub?  Hurry please!
Thanks,
eric

---

### Post by Tichondrius on 2006-01-30
Yeah, you should restore grub. 

To do that, boot from a knoppix live cd (download and burn it from knoppix.net if you don't have one handy). Then open a terminal, and mount your Ubuntu root partition, for example:

```
sudo mount /dev/hda1 /mnt/hda1
```

If your /boot directory in Ubuntu was on another partition (not the root partition) you shold mount it under the root partition. Again, only do this if your /boot directory was in a separate partition (which most likely it wasn't unless you specifically asked for it during the installation):

```
sudo mount /dev/hda2 /mnt/hda1/boot
```

Now reinstall grub:

```
sudo grub-install --root-directory=/mnt/hda1 /dev/hda
```

That's it, now you can reboot. Once you get into Ubuntu you can try adding FreeBSD to the grub menu by editing /boot/grub/menu.lst

btw, all the examples assume Ubuntu was installed in /dev/hda1 (first partition of first disk). If not, change he paths accordingly.

---

### Post by eric.stone on 2006-01-30
What a fantastic reply!  I happen to have a knoppix live CD on my desk.  I'll take me some time to do this so I'll get back to you tomorrow to let you know whether or not I was successful.
Thanks!!!!

---

### Post by ow50 on 2006-01-30
When adding FreeBSD to Grub, you might find the following thread useful.
[http://www.ubuntuforums.org/showthread.php?t=71540](http://www.ubuntuforums.org/showthread.php?t=71540)

---

### Post by eric.stone on 2006-01-30
A special thanks to you, as well, ow50!
Eric

---

### Post by eric.stone on 2006-01-30
A special thanks to you, as well, ow50!
Eric

---

### Post by Tichondrius on 2006-01-30
btw, this is also the SOP (standard operating procedure) after installing windows, because windows install always overwrites the boor sector so grub needs to be reinstalled afterwards.

---

### Post by eric.stone on 2006-01-30
Noted! Although, what got me into this learning experience was nooking wind@z and loading FreeBSD in its place as my dual boot.  Now if I can just understand the BSD culture!  For example, what is so much fun about having to  manually start x and then manually invoke the GUI of your choice?  I guess this should be taken up on a BSD forum.:D 
Many thanks.  
Eric

---

### Post by eric.stone on 2006-01-31
ow50,
I read the thread you referred me to - - I'm sure I can make it work, but how do I find out what partition I have loaded FreeBSD onto?  Before I upgraded to Breezy, ubuntu had an app called "disks" on the desktop that told me the names of the partitions and the type of format for each drive.  

Is there a partition reader program in ubunti or kubuntu?

Thanks,
Eric

---

### Post by Tichondrius on 2006-01-31
[QUOTE=eric.stone]ow50,
I read the thread you referred me to - - I'm sure I can make it work, but how do I find out what partition I have loaded FreeBSD onto?  Before I upgraded to Breezy, ubuntu had an app called "disks" on the desktop that told me the names of the partitions and the type of format for each drive.  

Is there a partition reader program in ubunti or kubuntu?

Thanks,
Eric[/QUOTE]

You can use fdisk to list all the partitons:

```
sudo fdisk -l /dev/hda
```

Or, if you want a graphical partition manager, install gparted (gnome) or qtparted (kde).

---

### Post by eric.stone on 2006-01-31
Cool!  I'm off to edit Grub . . .

---

