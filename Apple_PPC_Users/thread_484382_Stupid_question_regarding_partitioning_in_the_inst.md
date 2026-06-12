---
title: "Stupid question regarding partitioning in the installer"
date: 2007-06-25
forum: Apple PPC Users
---

### Post by sebbon on 2007-06-25
I am new to linux in general, and I have just decided to install Ubuntu. I have made the Cd, and I went into the installer, and I have been trying to install it. However, I want to keep my OSX partition. I have been messing around with the partitioning program in the installer, but I can't seem to get it right. It keeps coming up with an error message when I am trying to prepare the mount points.

[I]No root file system

No NewWorld boot partition was found. The yaboot loader
requires an Apple_Bootstrap partition at least 819200 bytes in
size, using the HFS Macintosh file system.[/I]

I am sure this is a very simple thing and that I am wasting your time. Sorry, but any help would be appreciated.

---

### Post by PCFascist on 2007-06-25
do you have a partition with the following mount point:

/


Just a first guess....

---

### Post by sebbon on 2007-06-25
Yea I had one of those as that...

but now I just realized that I had downloaded 6.10, so I am currently downloading Feisty Fawn.

Hopefully that will be easier.

---

### Post by ipx on 2007-06-25
Well, basically the easiest way is to partition your harddrive (with your favorite partitioner, i'd recommend gparted*) so that you have free unpartitioned space over. Then during the installation, you just simply choose "Use largest unpartitionated space".

* To use gparted the easiest way:
- Launch Ubuntu 7.04 with the live-cd (as you'd usually do when u install)
- Open a terminal (Applications > Accessories > Terminal)
- Type the following: 'sudo gparted'

This should launch gparted. :)

---

### Post by Leadtrombone2000 on 2007-06-26
i am having the same problem.  I have a G4 12 inch laptop and when i try to install from the live cd, i get the same message.

I have resized the partitions the way they shoul.  I hav tried to install with just a root patition and a swap partition in addition to my Mac OS partitions.  I have also tried to put in a boot partition.  but i always get the same message...:(

---

### Post by Auria on 2007-06-26
> **Leadtrombone2000 said:**
> i am having the same problem.  I have a G4 12 inch laptop and when i try to install from the live cd, i get the same message.

I have resized the partitions the way they shoul.  I hav tried to install with just a root patition and a swap partition in addition to my Mac OS partitions.  I have also tried to put in a boot partition.  but i always get the same message...:(

have you tried, as it has been already said, to leave empty space, and then install in empty space?

---

### Post by aantn on 2007-06-27
Ubuntu's default partitioner doesn't support HFS+ but Gparted does.

---

### Post by Leadtrombone2000 on 2007-06-28
Thats exaclty how i got it to work.  Thanks.

---

