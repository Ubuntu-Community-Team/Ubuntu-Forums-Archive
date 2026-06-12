---
title: "how do i resive my ext3 with gparted"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-01
my ext3 that is mounted at / only has 25gb or so, how do i get about 60gb of unallocated to join with the ext3, i have gparted and a gutsy live cd.

TIA
antisocialist

---

### Post by wolfen69 on 2008-01-01
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by antisocialist on 2008-01-01
as useful as that would be, i dont have the resize/remove option on the partion, is there anyway i can get it resized (screenie attached)

---

### Post by Xavieran on 2008-01-01
You need to unmount it first...right click on the partition in question and click unmount

---

### Post by antisocialist on 2008-01-01
i cant unmount it, it is / and it gives me the following error when i do try to unmount it:
The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

well, i dont have to resize the partition, i have 2 partitions that i am focused on, 1 is approx 25gb and one is 75gb ubuntu is in the 25gb one, i used gksudo nautilus and tried to copy my whole filesystem and all my files over to the partition i wanted (it was in a different nautilus window) and it said i cant copy something to its own location?! is there  a way i can switch the partitions, cu i plan to use more than 600mb more space

---

### Post by Xavieran on 2008-01-01
Are you running from a livecd? if not that would be why you cannot unmount it...

---

### Post by Xavieran on 2008-01-01
Is the 75 Gb one ext3 or does it have windows on it?
You will have to resize it though...you can't just copy your filesystem over...that would cause a few errors...

---

### Post by antisocialist on 2008-01-01
nope, the 75gb one has ext3, i want it to have windows, and ill try from a livecd, unmount and resize, hope it will work.

---

### Post by antisocialist on 2008-01-01
ok, i am booted in to the livecd, what do i do know, sudo aptitude install gparted and then run gparted?

---

### Post by jken146 on 2008-01-01
gparted is already installed on the live CD, so just run it.

---

### Post by az on 2008-01-01
You need to delete the sda3 partition to create free space.  Since it is within sda2, you will need to take that down, too.

Turn off your swap before you try to do this, since the live cd will use your swap.

sudo swapoff -a

Once the partitions are deleted, you can then extend your first partition over the free space.  Back up anything you had on sda3 before you delete it.

---

### Post by antisocialist on 2008-01-02
> **jken146 said:**
> gparted is already installed on the live CD, so just run it.

thanks, i got it, now all i got to do is get a dual boot menu (the thing where it asks you which boot to use

---

### Post by Henry Rayker on 2008-01-02
to get that "dual boot menu" you need to reinstall grub...

---

### Post by antisocialist on 2008-01-02
i did about an hour ago and i still dont have it, it defaults to booting into ubuntu now without asking me

---

