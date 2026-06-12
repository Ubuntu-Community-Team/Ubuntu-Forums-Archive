---
title: "Gparted issue: Putting Ubuntu on whole instead of partion"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by cybertron3000 on 2008-02-15
Hi ya'll, and by using ya'll, yes I'm an Okie.  I've got Ubuntu happily installed, and can say goodbye forever to windows (which I inadvertently erased by my own impatient curiosity once).

It is on a meager amount of space, so now I would like to have Ubuntu cover the whole hard drive without reinstalling it and having to rebuild the settings, etc. that I did to make it the perfect beast it is.  How can I do this in Gparted??  Thanks in advance - everyone who comes on this thing is such team players.:)

---

### Post by oldb0y on 2008-02-15
Boot up using the Live CD, and use gParted in that session to expand your Ubuntu-partition.

---

### Post by jan quark on 2008-02-15
if you have any important data make a backup first

then you can boot with the live cd and resize your partition

---

### Post by uberlube on 2008-02-15
What I find is the best way to partition Linux is to have your swap = 2wice your ram (thats pretty manditory) have a partition specifically for your root directory (usually 10-15 gigs) and then a seperate partition for your /home directory so just in case something happens to ubuntu or you want to upgrade to the new release. That is also where all your personal files and programs/settings are housed so if you have to do a clean install they wont be affected.  Of course this all depends on how much space you have.

---

### Post by aashay on 2008-02-15
Boot the livecd. Open up gparted. Delete every other partition and resize the ubuntu one (assuming it is the first one). Move the partition around if not. I You might also want to reinstall grub and edit the menu.lst file to point to the new ubuntu partition.

---

### Post by cybertron3000 on 2008-02-15
thanks everyone - I will try these ideas once I get the chance, let you know how it goes.

---

### Post by shadowmaster79 on 2008-02-15
Hi, 
first time it is best to know your hdd configuration after instalation.
I remember that LVM is not in default install of Ubuntu a then can show your config so:

sda or hda or ... 

sda1 - are windows partition
sda2 - linux boot, home, root ..... or swap
sda3 - linux boot, home, root ..... or swap
...

i use not gparted, i love command line....

before all action you should make backup of 
1. /etc
2. your /home/[username]
to any removable media - usb flash disk or anything other media

with this files can you on fresh install give back your configuration...

remember that /boot/grub/menu.lst and /etc/fstab have records for partitions that exist actualy.
After any change make check that all partiotions are with same number identifikator as before. when not repair grub and fstab file.

For you can best solution this....

1. convert fist partition sda1 (that with windows) to linux partition.
2. new sda1 format to ext3
3. boot from ubuntu cd
4. mount sda1 and other sda's to /mnt/ dir's
5. move data from sda2 sda3 to sda1
6. repair grub a and fstab (you have now sda1 with full system, another sda2... comment out wit #
7. reboot
if all success remove old partitions sda2 sda3 ... and expand partiton sda1 to full hd
remember to leave any space for swap.

i hope that can help you.

If you will more detailed checklist with step by step, write me.....

Bye

---

### Post by cybertron3000 on 2008-02-15
Thanks!  I booted the Live CD, and went with the option of putting a new Ubuntu on my largest partition of 45GB space.  I kept the previous Ubuntu install on the small space, and just tweaked my setting back to that again.:popcorn:

---

