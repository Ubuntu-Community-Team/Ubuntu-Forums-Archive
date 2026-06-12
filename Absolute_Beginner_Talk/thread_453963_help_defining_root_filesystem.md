---
title: "help defining root filesystem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Jesus4life0412 on 2007-05-24
hi

i partioned my single 80gb hdd  with gparted to do a dual boot with xp pro. i have a 55gb ntfs is the first partition, the second is a 18 gb ext3, and the third is a 2.75 linux swap. help me define this.

the mount points are /media/sda1 ntfs
                               /media/sda2 ext 3
                              none             swap

---

### Post by Ek0nomik on 2007-05-24
What do you need help with?

---

### Post by Jesus4life0412 on 2007-05-25
i need to figure out how to define the root file system so i can install in it

---

### Post by Ek0nomik on 2007-05-25
So during the install process you are stuck somewhere?

I guess I just don't know what you are stuck on in the install process.  The Live CD should just walk you through it?

---

### Post by Jesus4life0412 on 2007-05-25
it will not let me install ubuntu it says i need to define the root file system i dont know how

---

### Post by Ek0nomik on 2007-05-25
Ok, so you are using the Live CD?

Do you have Windows already installed and do you have data you can't lose?

If you have data you can't lose, defrag in Windows to try to get the data to the front of the drive.  Than reformat the hard drive so so you have a primary partition of NTFS first, than EXT3, than Swap.  (All primary).

Than just continue onto the next steps, and it will probably say to install on hd0, and just let it.

Reply if it works.  If you didn't know, you can use your Internet on the Live CD.

---

### Post by ffderrick on 2007-05-25
When you set the ext3 file size, you have to tell gparted that the drive is root or (/).
This is usually done automatically.  You may be trying the advanced install option.  Look again in gparted or the install program and look for the option to make the partition the root (/) partition.
Root (/) is the first directory of your partition and all other directories will be found there.
ie... (/home)  is the home directory on the root partition. and (/home/bob) is the bob directory of the home directory on the root partition.
Hope I didn't confuse you.
I will install from the CD to another drive and if your still having problems I will post a more specific fix to your problem.
Derrick

---

### Post by Jesus4life0412 on 2007-05-25
i backed up my data formated my drive and reinstalled windows and partioned my drive using gparted and have 3 partions ntfs,ext3,swap. and then tried doing a manuel install using the live cd 7.04. then just before the install on the install partitioner it tells me to define the root file system before it will let me install

---

### Post by Ek0nomik on 2007-05-25
What ffderrick said should definitely help.

Right click on your partition (ext3) and make sure it's / (/ means root partition) and I would place a boot flag on it as well.

---

### Post by Jesus4life0412 on 2007-05-25
will it still be ext3 if i formatted by make it root?

---

### Post by Ek0nomik on 2007-05-25
It shouldn't change the type of filesystem, so you should be good to go.

---

### Post by ffderrick on 2007-05-25
Root (/) is the designation of the partition.  ext3 is the file system type.
ie...   C\ is the designation of the windows partition and ntfs is the file system type. ( unders windows of course)

---

### Post by ahd khoury on 2007-05-25
when you are trying the manuall installation after you put the format to ( ext3 ) you have to change the                     ( /media/sda2 ) to  (  /  ) just  click on ( /media/sda2 ) and you will have other marks one of them are (  / ) click on it
and it will be ok 
i hope that would help it happend to me while i was trying to install ubuntu

---

### Post by Jesus4life0412 on 2007-05-26
thanks to everyone everything works now

---

### Post by mestrini on 2007-06-01
I'm facing similar problem although with some differences.

I have a master IDE1 HDD with WinXP with several ntfs partitions and a master IDE2 HDD with 4 partitions: ext3(7GB), swap(1.5GB), ext3(4.5GB), ext3(6GB), by this order.
The suggested root partition by gparted is the last one (6GB) which was a previous GNU/Linux /home and where i have personal data i want to keep and would like to use first partition (7GB) as root (as it was in previous installation)
This is where the problem comes as no matter what other ext3 partitions i choose the setup only stops displaying the "root file system" message and allows to proceed when i choose the 6GB (previous /home) partition.

Any ideas?

tx

---

