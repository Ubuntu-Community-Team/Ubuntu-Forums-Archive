---
title: "dreaded Grub 17 error NEWBIE HELP!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by shorty25 on 2007-10-19
i just tried to reinstall ubuntu fiesty so i could repartition it's drive (80gb second hdd)to give my windows hd (40gb first hdd) more space.  and now i get a grub 17 error.  i'm really new to linux so if anyone can please help me b4 my wife kills me b/c she can't get into windows it would be very appreciated!

---

### Post by alan34 on 2007-10-19
Set your pc to boot from the cdrom drive first.

Put in the windows cd and let it boot up the you should get to screen that has a repair windows
option. Pick go to the recovery consule, should ask you to login to a windows install and an administrator password.

You should then have      C:\WINDOWS      on your screen.

Type          fixmbr    and enter this will overwrite Grub and your PC should just boot up windows.

(type       exit       to leave the recovery consule)

Hope you have the windows cd or just borrow one good luck

---

### Post by Pumalite on 2007-10-19
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by shorty25 on 2007-10-19
> **alan34 said:**
> Set your pc to boot from the cdrom drive first.

Put in the windows cd and let it boot up the you should get to screen that has a repair windows
option. Pick go to the recovery consule, should ask you to login to a windows install and an administrator password.

You should then have      C:\WINDOWS      on your screen.

Type          fixmbr    and enter this will overwrite Grub and your PC should just boot up windows.

(type       exit       to leave the recovery consule)

Hope you have the windows cd or just borrow one good luck

i should be able to get one, this won't overwrite my whole windows hdd will it?  also afterwards how can i format the 2nd hdd to try and get ubuntu to dual boot again?  thanks!

---

### Post by alan34 on 2007-10-19
Should only repair your master boot record just dont install Windows!!!

I would reinstall ubuntu later just get windows working first give yourself plenty of time.

Iwould do a clean install if you have no important files on your existing ubuntu install.

When you come to partion the hard drives in the install make sure you pick hdb or sdb

for the install I would suggest you have 4 partions twice your ram as swap about 10GB for /   
about 20 GB for a /home partion then the rest have as a fat32 partion which you can see from
linux and windows.

:)

---

