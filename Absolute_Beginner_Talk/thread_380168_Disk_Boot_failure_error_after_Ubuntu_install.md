---
title: "Disk Boot failure error after Ubuntu install"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-03-09
Hi there,

I tried a search of the forums and didn't find an answer so I'm posting here.

I am interested in running linux/XP dual boot and attempted to set it up but now have this error:  'Disk Boot failure, replace system disk and press enter'

First: I had Mandriva One installed dual boot no problems but wanted to try this dist.  I let Mandriva take care of all partitioning and had set aside 20 gigs.  I uninstalled the lilo boot loader from the terminal using 'lilo -u' ('lilo -u' /dev/sda1 gave an error).  I used windows and it ran fine after.  


the story:

Installed Ubuntu 6.10 from the live desktop CD.

currently have: primary windows dev/sda1  (ntfs, primary partition)

I set the partitions and mount points as:
/    parition #2, 3gb,   /dev/sda2  (ext3, primary partition, directly after the windows partition)
(i didn't add the 'bootable' flag, perhaps this is my problem?)

one 20 gb extended partition with:

/swap partition #5 1gb /dev/sda5 (linux-swap, logical)
/home partition #6 15gb, /dev/sda6 (ext3, logical)
/media/fat32 partition #7 1 gb /dev/sda7 (fat32, logical)

grub was installed with the default setting in the installer, I think it was (hd0)

I made sure i didn't format /dev/sda2!

Now I get the error, is there anychance of fixing the master boot record?  I tried using my windows XP CD in recovery mode with 'FIXMBR' it said I had a non standard MBR, i fixed it, same error. 

I have the Linux SystemRescueCD if that will help, but I'm a complete novice.

Any ideas?  Worst case I'm hoping is that I install a new version of windows to the 20 gig partition to access my files on sda1 but I'm hoping I don't have to.

Thanks in advance,

Paul

---

### Post by Kateikyoushi on 2007-03-09
I would try to reinstall but this time format the sda2 partition if you try to install ubuntu there, (I can't see another partition where it could be be installed).

---

