---
title: "hard drive partitioning"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by pandorazboxx on 2007-06-18
hello all,

I just installed ubuntu on my pc as a dual boot system. I "had" a 120GB hard drive :-p

when i was going through the setup it was asking me about resizing my partition. So i set it to be "guided" and set it to 40.5GB. well, after that was all installed i went back into windows, ran the disk check it was bugging me about. And now i only have 40.5GB in windows for the C: drive as well!!

I was told by someone to try using the Gparted livecd. The only thing is i can't find any instructions about what to do when the gparted cd boots. 

i want to partition the hard drive such that say, 40GB goes to linux, while the other 80 remain for windows. Also i want to be able to share files between the two. I heard i had to use some ntfs-3g or something like that to allow me to do that part but i'll get to that later. for right now i just want my space back.

anyways, i need to know what i am supposed to be doing once i get into the gparted program??

i ran this line of code to find out how my disk was setup as of now. but i have no idea what any of this means

[IMG]http://img263.imageshack.us/img263/2133/screenshotln4.png[/IMG]

thanks for any help

---

### Post by irish_flu on 2007-06-18
The "resizing" you did was the Windows partition, not the Linux partitions (the Linux partitions didn't exist when you were doing that, only the Windows partition).  If you're willing to run setup again, when you resize the Windows partition set it to 80 GB instead of 40.

IIRC using the GPartd LiveCD will do the same thing.  The partition labeled HPFS/NTFS is where Windows lives.

---

### Post by pandorazboxx on 2007-06-18
thanks!! that's what i thought had happened, but now it is confirmed! thanks

---

### Post by dreadlord_chris on 2007-06-18
You're gonna have a real problem just resizing that NTFS partition - you will need to actually delete the partition(s) that come right after to be able to increase its size. I'd recommend deleting the Linux, Extended, and Swap partitions - then resizing the NTFS partition to the size you want. Then creating the Linux & Swap partitions.

---

### Post by pandorazboxx on 2007-06-18
so I should just delete the other partitions, then increase the ntfs size. Will this delete all the linux stuff, then i'll have to reinstall linux to set up the linux partitions?

---

### Post by dreadlord_chris on 2007-06-18
> **pandorazboxx said:**
> so I should just delete the other partitions, then increase the ntfs size. Will this delete all the linux stuff, then i'll have to reinstall linux to set up the linux partitions?

Yes,
yes,
yes,
and yes....

---

### Post by LaRoza on 2007-06-18
If you do that, you will not be able to boot into Windows, because grub is still there. If you re-install Ubuntu, this will no longer be an issue, Windows will be bootable.

Just in case, you might want to get the Super Grub Disk, which will allow you to fix the MBR in case you don't reinstall Ubuntu. (see my sig)

---

### Post by pandorazboxx on 2007-06-18
hmmm, i just used gparted live cd. decreased the size of hda2, moved it to the right, then filed up the rest of the space with hda1 and now everything if perfect again!!

this gparted thing is awesome. definitely not as hard as i thought it was. and i didn't have to delete anything

---

### Post by dreadlord_chris on 2007-06-18
> **pandorazboxx said:**
> hmmm, i just used gparted live cd. decreased the size of hda2, moved it to the right, then filed up the rest of the space with hda1 and now everything if perfect again!!

this gparted thing is awesome. definitely not as hard as i thought it was. and i didn't have to delete anything

lol.... well there ya go - good solution! the /dev points all stay the same, so GRUB doesn't get all confused...

---

