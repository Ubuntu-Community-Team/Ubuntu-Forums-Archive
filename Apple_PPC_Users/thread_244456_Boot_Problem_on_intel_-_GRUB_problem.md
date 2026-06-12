---
title: "Boot Problem on intel - GRUB problem"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by rohankaikini on 2006-08-26
Hi friends,

I recently installed Ubuntu 6.06 dapper on my intel.. dual boot.. with WinXP

Everything was working fine untill I started installing gfxboot as a bootloader. [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

I followed the instructions as given in the thread, but made a mistake in editing the menu.lst

So now, i have 'grub' uninstalled.. and gfxboot installed..
but the menu.lst has not been modified accordingly..

So, at boot, i get the grub cli i.e.
grub>

And now, i dont know what to do.. and how to edit the menu.lst.. or anything..
I am not able to boot to any of the OS..

Please help me on this ..
Thanks a lot in advance..

~rohan

---

### Post by v1ct0r on 2006-08-26
Ohh...ye old grub shell problem. 
There are two ways of solving this : 
1) use a linux live cd to edit your menu.lst
[the lovely [SLAX](http://www.slax.org/download.php) or ye Ubuntu Live CD ]. 

If this doesn't work i'll tell you #2. 
[but give us some detalis about your partition scheme first]

---

### Post by rohankaikini on 2006-08-26
> **v1ct0r said:**
> Ohh...ye old grub shell problem. 
There are two ways of solving this : 
1) use a linux live cd to edit your menu.lst
[the lovely [SLAX](http://www.slax.org/download.php) or ye Ubuntu Live CD ]. 

If this doesn't work i'll tell you #2. 
[but give us some detalis about your partition scheme first]
Hi v1ct0r,
great to see a reply..

well, i do have the Ubuntu live CD..
and i can very well boot with it.. but i'm not sure how to find and edit the menu.lst file.. (basically i dont know how to mount the linux partitions..)

can you tell me how can i give you my partition details from the grub cli?

All i know is that whenever i type 'root' at the grub cli, i get 
(hd0,2)

thanks,

~rohan

---

### Post by Aranel on 2006-08-26
I have absolutely zero experience with Macs (and I'm pretty new to Linux itself, heh), but hopefully I can give you *some* help. GRUB starts counting at 0, so the output for "root" means that what you want to mount is the third partition of the first hard drive. So say you wanted to mount it at /mnt/ubuntu...

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda3 /mnt/ubuntu
```

And that's it. You can edit your menu.list file from there (making sure you've got the one on your hard drive, not on the LiveCD ;) ) using Nano, Gedit, whatever. Good luck!

---

### Post by rohankaikini on 2006-08-27
> **Aranel said:**
> I have absolutely zero experience with Macs (and I'm pretty new to Linux itself, heh), but hopefully I can give you *some* help. GRUB starts counting at 0, so the output for "root" means that what you want to mount is the third partition of the first hard drive. So say you wanted to mount it at /mnt/ubuntu...

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda3 /mnt/ubuntu
```

And that's it. You can edit your menu.list file from there (making sure you've got the one on your hard drive, not on the LiveCD ;) ) using Nano, Gedit, whatever. Good luck!

Hey Aranel..
Thanks for the quick and wonderful solution.. worked like a charm!!
:-)..
now everything is bck to normal..
~rohan

---

