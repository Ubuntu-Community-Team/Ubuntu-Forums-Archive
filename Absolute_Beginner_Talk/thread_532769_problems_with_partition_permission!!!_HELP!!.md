---
title: "problems with partition permission!!! HELP!!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by lanchongzi on 2007-08-23
hi to all of you


I have been searching for about two hours now
but can't find anything useful :(

my problem is as follows
my friends PC had a virus struck Windows installed
so I offered him Ubuntu instead - he liked that idea and asked me to get rid of windows BUT to leave his data untouched
his HD was split in 4 parts ( C: with windows OS on it, D:, E:, F: containing data )
so I installed Ubuntu above C: and formatted in the install process.
now Ubuntu runs perfectly   JUST  the former D, E, F are just read and protected.
I need to open them and treat them as his new drives to store his data on

also the data on it is not change able

i tried "gksudo nautilus "  thats about all i had up my sleeve :(

doesnt work

so  -   how do i get them to be open and fully useable??????

do i have to use 'gparted' and change something about them inside there????


please help me  - he can look like a devil when he gets mad...


thanks in advance  :)

---

### Post by 505 on 2007-08-23
The file system on D, E, and F is probably NTFS (check GParted to be sure). NTFS is Windows NT/2000/XP preferred file system, but read/write support on Linux is not that good. You can read it without a problem, writes is more of a challange. You can install the ntfs-3g drivers, to enable write support. However, these drivers are experimental. If your friend really likes Linux it might be better to format the drives and changes them to ext3.

---

### Post by lanchongzi on 2007-08-23
do i really have to format them???

cant i just use gparted to change them???


because since it is just read i cannot back up the data!!

headache...

---

### Post by r_l on 2007-08-23
Assuming that you are using Feisty, see what happens when you try this:

[URL="http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html"]
http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html[/URL]

---

### Post by glotz on 2007-08-23
Do a **sudo fdisk -l** to see what drives there are. (that's a small 'L' not number 1)

---

### Post by quinnten83 on 2007-08-23
> **lanchongzi said:**
> do i really have to format them???

cant i just use gparted to change them???


because since it is just read i cannot back up the data!!

headache...

actually they say now on the ntfs-3g site that their software is stable, youcould just install it. It will automatically mount the ntfs partitions
to be on the safe side, i would copy the data to an external disc.

---

### Post by lanchongzi on 2007-08-23
i will try the link now


thanks

---

### Post by lanchongzi on 2007-08-23
i follwed the link above

but it doesnt let me choose the drives  just if it is internal or external...

anyway the " locked " sign is gone  - good so far  :)

so oi tried to install google earth  - it said i don't have permission to write on the disk

so it didn't work

also if i want to move the files it says somethging in chinese

because my friend is chinese so the language is also set to it

bottom line is that i can't copy his data - not even to his own home folder...


any ideas???

---

### Post by r_l on 2007-08-23
> **lanchongzi said:**
> i follwed the link above

but it doesnt let me choose the drives  just if it is internal or external...

anyway the " locked " sign is gone  - good so far  :)

so oi tried to install google earth  - it said i don't have permission to write on the disk

so it didn't work

also if i want to move the files it says somethging in chinese

because my friend is chinese so the language is also set to it

bottom line is that i can't copy his data - not even to his own home folder...


any ideas???
I am sorry that I don't understand exactly what you mean.  If you try to install something, it means that you are using C drive, right?  So you mean you have permission block on C drive? Have you tried to write to other drives see it is writable (e.g., to create an empty folder there.)   How did you install Google Earth - by downloading deb (then it will ask you for password), using apt-get (then you will need the sudo prefix), or using some other ways?

---

