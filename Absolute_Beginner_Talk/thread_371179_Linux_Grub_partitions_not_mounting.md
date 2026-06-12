---
title: "Linux Grub partitions not mounting"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-02-26
Okay, well first off, even though i absolutely hate windows, i ended up installing it and ... as usual it messed up my computer in some way. It ended up copying over the GRUB, thus making it impossible to open Ubuntu. Anyway, i used the Super GRUB iso, booted and reinstalled GRUB successfully, but when i try to boot from the right partition, i get the following error:

> [http://img356.imageshack.us/img356/2671/00008js5.jpg](http://img356.imageshack.us/img356/2671/00008js5.jpg)

sorry for the quality, i had to take it with my digitial camera. Anyway, if i mess around in Supergrub i can boot ubutntu fine (which is how im using it now). 


So, how can i get this partition to "mount" even though, it must already be mounted if the GRUB in SuperGrub can boot it?, no?

---

### Post by chggr on 2007-02-26
I think you've set up Grub to boot in the wrong partition.
Check the file /etc/menu.lst and make sure that the Ubuntu option has the proper "root" entry (the partition where the Linux filesystem is located)

To assist you, I will paste now the ubuntu entry inside my menu.lst file. I have ubuntu installed on hda6 (hd0,5 is equals /dev/hda6).

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

---

### Post by KIFIKA on 2007-02-26
hmmm, i dont have a /etc/menu.lst file.. anything else this might be named?

---

### Post by annda on 2007-02-26
look here:

/boot/grub/menu.lst

plus i highly recommend this to anyone looking for files:

```
sudo updatedb
locate the_name_of_the_file
```

---

### Post by KIFIKA on 2007-02-26
Not sure, if this is right, but here is what it said. If so, what do i change? The harddrive im trying to boot off of is an 80 gb hdb1. Also, my menu.lst showed alot more from when my 40gb (the one that has windows :( now ) used to run ubuntu, if i just delete it, will it remove it from the grub so it will boot without making me wait or click?

```
title		Ubuntu, kernel 2.6.17-11-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot
```

---

### Post by annda on 2007-02-26
to the best of my imagination (i never tried such a bold move) deleting you grun menu.lst will result in serious trouble.

i recommend  following the instructions in this thread
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
to get things back in order.

good luck!

---

### Post by KIFIKA on 2007-02-26
Ugh, okay, i did everytrhing in that tutorial and it didnt work.. then i found another way to start Ubuntu.. but this way just seemed so insane, that if i explained it... idk I recorded my screen so i could show you guys what exactly happened. I will also try to explain the video too. 

Okay, as i said before i have 2 harddrives, one that once had ubuntu, but now has windows. Okay, well as you guessed it the grub files from the ubuntu are there, they wont load it says file not found (because it was deleted)... but the memtest from that harddrive works. When i run the memtest, i hit escape... then when i boot up again, it boots ubuntu. If i shut it off and try to boot from that grub, i get the errror 17 again, unless i do the memtest .. rinse and repeat... 

do i have to do this everytime i want to run ubuntu? Can someone help me?

the video is only 52 seconds long, and end right before UBUNTU is about to start back up. You can view it here:
[http://www.youtube.com/v/ycJUyGpszF4](http://www.youtube.com/v/ycJUyGpszF4)

sorry it took so long to reply, i hope your still checking in and on the forums :P

---

### Post by chggr on 2007-02-27
> **KIFIKA said:**
> hmmm, i dont have a /etc/menu.lst file.. anything else this might be named?

Sorry, my fault here!! :(

---

### Post by Duck2006 on 2007-02-27
From the terminal

sudo fdisk -l 

and post the out put here

---

