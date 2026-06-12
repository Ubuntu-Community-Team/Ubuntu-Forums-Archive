---
title: "HDD problems"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by IndiShukla on 2007-08-26
Hello
First I would like to introduce myself. I have been using Windows my whole life and finally decided to give linux  a go! Im willing to take time and learn and become as comfortable with ubuntu as I am with windows and hopefully even better. 
ok now to the problem

So I have 2 hard drives.  1 for the os and the other for backup and just where I keep all of my stuff. Now I went through the ubuntu setup without a hitch telling ubuntu to use the 1 hard drive for the os. Now I already formatted my other backup HD to ext3 and transferred all of my stuff on there. 

Ok ubuntu is installed and I try to access my backup hard drive. After about 30sec the whole system just freezes and I am forced to restart. The same thing happens everytime I try to access that HDD. 

Next I plan just to ditch the backup HDD because it has been giving me contant problems when I tried formatting it. So I assume that it is bad. Now im trying to use 1 the 1 HDD for everything. I then learned that Im not allowed to do anything to the os hdd becuase there is some lock on it from ubuntu that won't let me create new folders and such. Now I want to partition the hard drive 1 section for the os and the other for my stuff. I tried using the partition manager from the ubuntu live cd and it really didn't work. I made the os partition 75gb and left the rest of the space for my other stuff. When I started installing again ubuntu put its file system on both partitions and im not allowed to add/delete things from the partition. 

What can I do? 
I feel really stupid for asking this but I have tried so many combos of things that I just want an answer so I can start using and enjoying ubuntu. 

Thank you to anyone who can help me! 
ps: sorry about bad grammer and spelling I am typing this up fast.

---

### Post by pgar23 on 2007-08-26
if you are using ubuntu gnome, you could try
```

sudo gksu nautilus
```
this will allow you to add/copy/delete files...if this is what you are asking

---

### Post by pgar23 on 2007-08-26
or just ALT>F2 
```
gksu nautilus
```

---

### Post by IndiShukla on 2007-08-26
hopefully that will work
thank you

---

### Post by IndiShukla on 2007-08-26
is there any partitioning program that someone would suggest im not having much luck with the one on the live cd

---

### Post by Hobo Joe on 2007-08-26
Are you talking about GParted?

Cause in my opinion it's a fantastic program.

---

### Post by IndiShukla on 2007-08-26
its great but whenever I partition a drive it installs ubuntu on both (not sure if it is supposed to) and then I can't touch both partitions except for using the code that was provided above. 

Whenever I try to even copy the data from my back up HDD ubuntu freezes so I need to find a way to transfer the data from my backup to my primary os HDD without freezing.

---

### Post by meierfra on 2007-08-26
Could you post the output of

```
sudo fdisk -l
```

and 

```
cat /etc/fstab
```

It might help us to figure out  why you cannot perform add/delete.

---

### Post by IndiShukla on 2007-08-26
just an off topic question. When I do partition my HDD should I make the partition that will store all of my non os stuff in fat32 or ext3 or any for that matter? What would be the best?

---

### Post by por100pre1 on 2007-08-26
> **IndiShukla said:**
> just an off topic question. When I do partition my HDD should I make the partition that will store all of my non os stuff in fat32 or ext3 or any for that matter? What would be the best?

Fat32 is the best alternative if using Windows and Ubuntu, for example. Only works with files up 4GB. Ext3 is best for Ubuntu only, can't be seen by Windows without a special driver. NTFS is best for Windows, Ubuntu can read it OK, but write can be risky.

---

### Post by IndiShukla on 2007-08-26
alright now I have partitioned my 1 hard drive and transferred my data onto it. Now for the install of ubuntu: I go in and choose to do a manual partition. I choose the free partition that I want ubuntu on and now whenever I try going forward it gives me an error about my mount point:

It says:

Error no root file system is defined. Please correct this from the partitioning menu

What type of mount point should I use? This partition is going to be 75gb out of 400gb (don't know if this will change what type of mount point.) and will hold ubuntu

edit: also whenever I choose the mount point as "/" it says:
File system was not cleanly unmounted! You should run e2fsck, Modifying an unclean file system could cause severe corruption

---

### Post by IndiShukla on 2007-08-26
woops nevermind I figured the part I just posted about out

---

