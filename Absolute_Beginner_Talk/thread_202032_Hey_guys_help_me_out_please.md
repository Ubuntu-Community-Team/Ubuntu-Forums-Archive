---
title: "Hey guys help me out please"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by bparkin on 2006-06-22
So heres the deal:

Windows on raid(2 wd's).

I had a samsung drive(112 GB). I use it to store a bunch of movies,music,shows, etc... so I partitioned 510 MB for swap (linux swap, is that okay?) and 2.1gb at the end before the swap ext3 all using Paragon Partition Manager.

I didn't think I needed more space, but apparently after automatix it's out of room. 

1. Does the 'filesystem' refer to my 2.1 GB partiton and where is my swap partition can I view that somewhere?

2. What should I do about running out of space? i'm confused, I can view my samsung drive(unbuntu putit on the desktop) and all that, but it apears automatix is installing stuff to the filesystem so I have no idea what I should be doing, how do I extend my filesystem partition?

thanks

---

### Post by Winblowz on 2006-06-22
So let me verify this...You have a root partition which is 2.1GB (using ext3) and a swap partition of 510MB? Could you please post the output of 
```
nano /etc/fstab
```
You can just copy and paste if you like:)

---

### Post by bparkin on 2006-06-22
Thanks for the response, ill reboot to unbuntu and try it out

---

### Post by bparkin on 2006-06-22
Okay yes you are correct with your Q winblowz (I made partitions on the end of the samsung drive with paragon)

but big problem tryin to log in: tried to log in  and it just kicked me back into login, tried doing terminal login thingy and it kicked me with a error as follows:

GDM could not write your authorization file. THis could mean that  your out of disc space or that your home directory could not be opened for wirting. IN any case it's not possible to log in. 

haha thanks unbuntu.

Any help anyone? I'm in windows right now.

---

### Post by mlind on 2006-06-22
Did you make 2.1GB for ubuntu root (/) partition ?
I think that's not big enough.. How did the install go?

I reckon you must make new partition, atleast 5-6GB. I hope you did a separe boot
partition or used lvm, or this will be bit tricky.

Anyway, you need to make chunk of free space, allocate it as ext3, mirror your whole
system there (using tar maybe), chroot to new root folder and fix grub and
/etc/fstab.. sounds like pain.

---

### Post by bparkin on 2006-06-22
Darn, I thought 2 GB would be enough for the filesystem, just like windows, you can throw all the extra stuff on an aux drive/partition. 

I always thought linux was supposed to be small/quick. I mean the install cd is only 600 MB, not close to 2 GB, I'm confused.

---

### Post by mlind on 2006-06-22
[QUOTE=bparkin]Darn, I thought 2 GB would be enough for the filesystem, just like windows, you can throw all the extra stuff on an aux drive/partition. 

I always thought linux was supposed to be small/quick. I mean the install cd is only 600 MB, not close to 2 GB, I'm confused.[/QUOTE]

Ubuntu server install probably would fit very nicely, but current Ubuntu desktop
doesn't. linux can actually very small and quick, I run one on my ipod which fits to
~128MB.

Reading [release notes]("http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3") before doing a fresh install of new OS is considered as good practice,
because system requirements can vary a lot

---

### Post by nalmeth on 2006-06-22
with the full ubuntu-desktop (gnome GUI and it's application) 2 gigs is not enough.

Xubuntu might fit on that, or server install with fluxbox or another minimal Desktop will fit, but not the ubuntu/kubuntu-desktops

---

### Post by bparkin on 2006-06-23
so you would suggest a repartition/reinstall with what, 4 GB?

---

### Post by mlind on 2006-06-23
[QUOTE=bparkin]so you would suggest a repartition/reinstall with what, 4 GB?[/QUOTE]

I depends on your requirements. if minimum requirements are ~3GB, and you
ever plan to build something or install additional software, I'd start atleast with 5GB.

Easiest thing is probably to backup your /home folder, increase slack space with your
preferred partition tool and install Ubuntu from scratch.

---

### Post by bparkin on 2006-06-24
well I tried to log in failsafe and this came up:

"GDM could not write your authorization file, this could mean that your out of disc space or that your home directory could not be opened for wirting. In any case, it's not poossible to log in."

any ideas?

---

