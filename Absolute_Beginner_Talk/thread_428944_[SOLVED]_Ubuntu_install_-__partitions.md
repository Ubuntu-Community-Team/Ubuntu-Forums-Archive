---
title: "[SOLVED] Ubuntu install -  partitions"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-30
I have a 160 GB of HDD. This is how i want the partitions:
 
C:\ - Windows - 25GB
D:\ - Windows Data - 25GB
 
/ - Ubuntu root - 9 GB
/home - 20GB
/swap - 1GB
 
/shared - (remaining space ~70GB) 
 
I know all of above doesnt add up to 160, thats because using 1024MB per GB I get only 150GB of available space.
 
I also plan to install Kubuntu later. One at a time however, so for now I am **only** installing Ubuntu.
 
Now a few questions:
 
1) Can i put Drive D: as an extended partition in C: itself ? If so how can i do it in Vista? Or can I do this through the Ubuntu partitioner?
2) Does the /(root) have to be a primary partition? if not, what is recommended?
3) Should /home be a primary partition? if not, what is recommended?
4) Can I use the same /home between Ubuntu and Kubuntu ? I am planning to use the same /swap for them.

---

### Post by Spike-X on 2007-04-30
The easiest way to do it would be to set your C: and D: partition sizes in Vista, then set the rest of the HD as free space. From there, install Ubuntu using the manually edit partitions  option.

---

### Post by bobplano on 2007-04-30
for that kuubntu install you don't have to worry about much. it's just a desktop enviroment so it just goes over the kernel, which is the same for (x)(k)(ed)ubuntu. just run 
```
sudo aptitude install kubuntu-desktop
```
the easiest way for partitions would be windows makes windows and ubuntu makes ubuntu and shared. make the shared FAT32 since both can read it easily

---

### Post by Inxsible on 2007-04-30
> **Spike-X said:**
> The easiest way to do it would be to set your C: and D: partition sizes in Vista, then set the rest of the HD as free space. From there, install Ubuntu using the manually edit partitions option.
 
I currently have the C: and D: drives as you mentioned and the rest unallocated. But Vista says that D: is also a primary partition. I was wondering if I can make it an extended partition within C. 
Or am I totally wrong? Since C: would need to be a primary partition (since it boots Windows)and i cant put any other partitions within it.
 
a lil confused here :confused:

---

### Post by Inxsible on 2007-04-30
> **bobplano said:**
> for that kuubntu install you don't have to worry about much. it's just a desktop enviroment so it just goes over the kernel, which is the same for (x)(k)(ed)ubuntu. just run 
```
sudo aptitude install kubuntu-desktop
```
the easiest way for partitions would be windows makes windows and ubuntu makes ubuntu and shared. make the shared FAT32 since both can read it easily
 
I know that we can install Kubuntu within Ubuntu or vice versa....However, I would like to keep them as separate installs since i plan to get rid of one...depending on which one i like better :)

---

### Post by bobplano on 2007-04-30
the C:\ isn't the fourth primary partition so it can't be split into extended partitions. it should be fine, just make swap an extended partition. as for the kubuntu ubuntu thing you can just use that command and then use 
```
 sudo aptitude remove ubuntu-desktop (or gnome-desktop i don't remember)
```
or just reverse the other command

---

### Post by Inxsible on 2007-04-30
> **bobplano said:**
> the C:\ isn't the fourth primary partition so it can't be split into extended partitions. it should be fine, just make swap an extended partition
 
Ok Cool. 
So I would have the following:
 
C: - primary partition
D: - primary partition
 
Extended Partition:
    Logical 1 = /
    Logical 2 = /home
    Logical 3 = /shared data
 
One more partition I can use later for Kubuntu
 
Correct?

---

### Post by antoz on 2007-04-30
That looks OK but you will still need another logical partition for "swap" though.

---

### Post by Inxsible on 2007-04-30
> **antoz said:**
> That looks OK but you will still need another logical partition for "swap" though.
 
Correct. my mistake !

---

### Post by GrueTamer on 2007-04-30
> **Inxsible said:**
> Ok Cool. 
So I would have the following:
 
C: - primary partition
D: - primary partition
 
Extended Partition:
    Logical 1 = /
    Logical 2 = /home
    Logical 3 = /shared data
 
One more partition I can use later for Kubuntu
 
Correct?Everything looks alright except for "One more partition I can use later for Kubuntu, Correct?".  You don't need another partition if you do the ```
sudo apt-get install kubuntu-desktop
```, or if you do the ```
sudo apt-get remove ubuntu-desktop (or kubuntu-desktop, if you want to remove that)
```.  Kubuntu is just ubuntu with a different desktop environment.  You boot the different desktop environments by changing the session type at the boot splash (probably the options menu or the sessions menu, something like that).  Dealing with kubuntu through the terminal is a lot quicker and easier than having a separate partition for it, and you get to keep all your documents where they should be also.

---

### Post by Inxsible on 2007-04-30
If I change the mount point of the Windows partition, that wont be a problem right ?
 
Currently it shows 
/media/sda1
/media/sda2
 
I want it to be
/windows/sda1
/windows/sda2

---

### Post by GrueTamer on 2007-04-30
> **Inxsible said:**
> If I change the mount point of the Windows partition, that wont be a problem right ?
 
Currently it shows 
/media/sda1
/media/sda2
 
I want it to be
/windows/sda1
/windows/sda2You could make the partitions mounted at whatever you want them to be, but to avoid confusion, I would recommend /media/windows/sda1/2.  To mount them like this, in the terminal, type ```
sudo mkdir /media/windows/sda1 && sudo mount /dev/sda1 /media/windows/sda1 && sudo mkdir /media/window/sda2 && sudo mount /dev/sda2 /media/windows/sda2
```

You only need the mkdir parts the first time.  If I made a mistake while typing that, please tell me and Inxsible, I wouldn't be surprised if I missed something :)

---

### Post by antoz on 2007-04-30
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

I found this link very helpful in the past.

---

