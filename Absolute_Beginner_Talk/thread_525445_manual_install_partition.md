---
title: "manual install partition"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-08-14
i think i'm close but what do i need for mount point?
use as: reiserfs is done 

swap is allready done for other linux app on this drive
do i need another swap?

---

### Post by Inxsible on 2007-08-14
> **trucker33377 said:**
> i think i'm close but what do i need for mount point?
use as: reiserfs is done 

swap is allready done for other linux app on this drive
do i need another swap?

you can mount the drive like ```
sudo mount /drive_name /mount_point
```

and no you dont need another swap, but during installation make sure you point the new install to the same swap.

---

### Post by trucker33377 on 2007-08-14
OK  now it says no root system is defined.

would i be better off if i unhooked 1 drive and re-hooked after i install this?

---

### Post by az on 2007-08-14
Why don't you just pick guided partitioning?  What specific needs do you have to do it manually?

---

### Post by trucker33377 on 2007-08-15
i have 2 HD's one is 250 gig other is 120 gig i want this on the 120 gig drive.

 it showed both drives and picked the 250 gig to instill there was nothing i could change, so i fig i could setup manully.

 but i didnt know just how to do this. at any rate i unhooked the 250 drive and set up on the 120 like i wanted, now i have win xp on one drive 
and vector, kubuntu on ther other.

 but in doing this grub has been setup on 2nd drive for kubuntu and vector from th kubuntu install

 vector was setup with both drives hooked up before kubuntu was installed it setup grub for xp and its self. useing lilo grub


 when i boot the computer i see win xp ,dos,linux,linux-gui,linux-tux. not real sure about that last one but its somthing like that.

 at any rate all linux lead to vector. the last one linux-tux puts me in the vector termmal for command line.

 dos works but i dont know how to use it , says use tab key for options. that just show all the same things that lilo window has to pick from. i know partition is there i can see it from fdisk with both HD hooked up,

i think i may be in a bit over my head on this
bottom line is i want xp on 250 gig hd
kubuntu on 120 gig hd
vector is temp i just waant to learn how to use it.
im thinking maybe i should have added kubuntu 1st then vector.

both are new install so wiping 2nd Hd and restarting is no big deal

---

