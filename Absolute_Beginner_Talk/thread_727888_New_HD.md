---
title: "New HD"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Dabbill on 2008-03-18
I am considering getting a new HD for my Ubuntu box. Currently i have a 60gig in it. I am looking to go to like a 160gig or 250gig. I have /root, /home on seperate partitions on that drive. Is where a way to image that drive to a new one even tho its a different size with out loseing any configurations or installed apps. Dont reall wanna start over. I am guessing that I want to boot a live CD with just the new HD in the computer and setup the partitions, but then not sure how to get the data over from 60gig to the new HD. Also the 60gig HD is IDE, new HD will be SATA. So i do know i will have to edit FSTAB and grub config before the computer would boot on the new drive.

---

### Post by hyper_ch on 2008-03-18
just copy the stuff with the permissions:

```

sudo cp -Rp /home/* /media/new_drive/home/

```

the same with the /root partition

and then alter the fstab and change the mounting to the new drives for those two folders.

---

### Post by philinux on 2008-03-18
This

[http://www.remastersys.klikit.org](http://www.remastersys.klikit.org)

can do it.

---

### Post by Dabbill on 2008-03-18
hyper_ch to make sure i got this correct, or if not correct would this work.

1. Boot computer with new drive as a secondary.
2. Creat the partitions as i want them on the new drive.
3. use the cp command and just copy those to the partitions where they need to be set.
4. Edit the FSTAB / Grub config to the new partitions. 
5. Restart the computer with just the new drive in the computer?

That sounds like the route your saying.

---

### Post by hyper_ch on 2008-03-18
pretty much it is...

however if you want to copy /home onto hdXY, then you will copy this
 ```

sudo cp -Rp /home/* /media/hdXY/

```
as you will mount it then as /home

---

### Post by Dabbill on 2008-03-18
I just copied the date over to the new drive. Changed the FSTAB and grub menu uuid numbers. All i get now when i try to boot is a blank screen.

---

### Post by hyper_ch on 2008-03-18
then you did something else.... because grub starts before fstab

---

### Post by Dabbill on 2008-03-18
Well i reinstalled grub, now i get the grub menu. Then it goes to the ubuntu splash screen. Sits there for like 10secs then just goes to a black screen. The bar doesnt move at all on the ubuntu splash screen.

---

### Post by Dabbill on 2008-03-18
Not sure if this makes any difference. My old HD had 3 partitions.. /, /boot, and /home. My new HD also has 3 partitions ... swap, /, and /home. I reinstalled grub so that should fix the issue with no longer haveing a seperate /boot partition.

---

