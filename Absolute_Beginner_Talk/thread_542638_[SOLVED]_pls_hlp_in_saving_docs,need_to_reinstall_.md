---
title: "[SOLVED] pls hlp in saving docs,need to reinstall ubuntu,dont have seperate /home par"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-09-04
hello there

i need to reinstall Ubuntu.

unfortunately i had not created a seperate home partition. so now i am in trouble.

my current partition config is:

/dev/sda1 = windows fat32 partition 4 GB
/dev/sda1 = swap 512 MB
/dev/sda2 = root(/) ext3 all rest space.

i don't have any portable hard disk or high capacity hard drive so can not save data through them.

any help anyone....

any possible way of saving data like by merging partition from windows by using partition magic or anything else....

have tried partition magic..... it doesn't merge windows file systems like fat and ntfs with linux file systems like ext3

---

### Post by mlentink on 2007-09-04
Can you still boot into Ubuntu? I guess not, or you wouldn't have this problem.
Can you boot into Windows on that machine? If so, there's not too much of a problem either
Download and install in windows ext2fs ([www.fs-driver.org](www.fs-driver.org)) which will allow access to the linux partition from windows. You can then e.g. burn it on a DVD or something.

---

### Post by logos34 on 2007-09-04
You can't 'merge' partitions.  

Use Gparted on the ubuntu live cd to shrink sda2 down as much as possible.  Delete swap.  Then expand fat32 sda1 into the free space.  Copy over all your files to sda1.  (or boot into windows and do it there.)

edit: yes, and you'll need fs-driver...And DVD might make more sense IF you have a dvd-burner, which I assumed you don't since you didn't mention it)

---

### Post by cyneuron on 2007-09-04
thanks for all ur responses....

i can boot into ubuntu.... i am reinstalling because there is some problem occuring in trying to install kubuntu -desktop in ubuntu. KDM isnt working and not allowing me to boot into graphical mode.....(though GDM is working fine, but i wanted to use kubuntu on KDM only) i have tried reinstalling kubuntu-desktop many times, but same problem, most probably because the screwed up KDM setting are still preserved even when i remove while kubuntu desktop...

finally i decided to reinstall the things....have backed up updates and installed debs, via aptoncd....so reinstallation wont be a problem.....

this idea copying data to fat32 ad then shrinking ext3, then expanding fat32 from available free space, by using gparted looks promising...

i have gparted installed in ubuntu... will this work only from live cd.... gonna try it from installed system itself.... and report back....

---

### Post by mlentink on 2007-09-04
No, you cannot run GParted from an active partition. Use the LiveCD instead.

---

### Post by cyneuron on 2007-09-04
yaa, sorry for this dumb assumption of being able to run gparted for resizing from system...

thanks a lot for this idea of using live cd for resizing and saving docs....

though it took good amount of time in repeated resizing, then rebooting for transferring the 
data

surprisingly i couldn't transfer data on newly created partition in live cd. Why ? any idea...

well finally i got things sorted out....

livecd is a prime example of power ofLinux.....

thanks again....

---

