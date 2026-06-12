---
title: "Cannot access second hard drive"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by emineo on 2005-05-14
well first off, i just installed Ubuntu and it rocks! 

secondly, the problem, 

the hard drive is detected and shown but when i try to access it i get the following message:

$ sudo mount /dev/hdb /media/windows/
mount: /dev/hdb already mounted or /media/windows/ busy


i get the same message when i try opening via the gui way.

any help will be greatly appreciated. thank you!
                                                   
                                                   Sincerely,
                                                           the man with 9 kids  :^o

---

### Post by blueplazma on 2005-05-14
Take a look in your /etc/fstab file.  It might be mounted already in /media, which is the default Ubuntu mount point.

---

### Post by emineo on 2005-05-15
yes the init.d file does contain the hard drive but im not able to access it at all

even without doing a  "mount" command, im unable to open it via nautilus

---

### Post by fng on 2005-05-15
To be sure its allready mounted, just type 'mount' in a terminal
This will show all the mounted devices

---

### Post by JimmyBEng on 2005-05-17
I  might be wrong, but you are mounting a partion of the second hard drive, so shouldn't it be something like:

$ sudo mount /dev/hdb1 /media/windows/

with the 1 after hdb (or whatever the right number is for your partion) so that you say which partition you are mounting.

---

### Post by davidmigl on 2005-05-17
[QUOTE=JimmyBEng]I  might be wrong, but you are mounting a partion of the second hard drive, so shouldn't it be something like:

$ sudo mount /dev/hdb1 /media/windows/

with the 1 after hdb (or whatever the right number is for your partion) so that you say which partition you are mounting.[/QUOTE]
 What permissions does a user need to have to access the drive, and how would he go about setting these?  I cant mount the drive OK, but Ubuntu tells me that I don't have the appropriate permissions.  I know I could just do this in root, but I don't want to have to logout/login just to access a HDD.

---

### Post by robert114 on 2005-10-19
I've had simular problems after compiling my own kernel so I'm not sure, but maybe it will help you.

I just removed the EVMS package and my HD mounted beautifull.

---

### Post by Tass on 2005-10-22
Hi

I think I've got the same problem.  I've mounted the drives, and I can see them in the places pane, in the filebrowser, but can't access them.

If I go to System > Administation > Disks, select the partition and click browse, however, I can browse them without a problem.

Looking at the properties of the shortcuts in the places pane, the owner is root.  This seems to prevent me from changing anything on the disk.  When reading through the FAQ, there are instructions to mount an NTFS drive with read-only access, and mount a FAT or FAT32 drive with full access.  Does this mean that NTFS can't be mounted with full access?

Thanks,

Tass

---

### Post by jack-78 on 2005-10-22
I've mounted my NTFS disk following this guide: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs) and everything works fine.
Maybe it will help you guys

---

### Post by lord~spidey on 2006-11-22
im a n00blet and i got ubuntu not long ago and my win xp drive is not detected :( 

i love ubuntu but i wish you could just double click on an  apps to install them that would own [-o<

---

### Post by bodhi.zazen on 2006-11-22
> **lord~spidey said:**
> im a n00blet and i got ubuntu not long ago and my win xp drive is not detected :( 

i love ubuntu but i wish you could just double click on an  apps to install them that would own [-o<

Interesting place to post.

Try synaptic

---

