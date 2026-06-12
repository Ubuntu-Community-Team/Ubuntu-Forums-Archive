---
title: "frustrated"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by HiTmE on 2006-04-29
>.< i've just finish downloadin the ubuntu software burned the iso got it workin my old compaq presario. everything is going good intill it goes to partition disk. now it gets stuck at a point and tells me that there is no file root system. so i go back do the same thing and i have no clue how to fix it could any one tell me what i'am doing wrong or what i could do to fix this?

---

### Post by Kethinov on 2006-04-29
Are you manually partitioning? If so, you need to explicitly define which partitions represent which mount points in Linux. If you're not so sure what all that means, the best thing to do is to not bother with manually partitioning, but instead to use a clean hard drive just for Linux and let Ubuntu erase the entire disk and do it for you.

---

### Post by PhilOSparta on 2006-04-29
Are you using the "install CD"?

When you get to the partition section of the install, one of the selections is
"mount point".  You have to have / as the mount point for the partition that you want Ubuntu installed.

---

### Post by Jason_25 on 2006-04-29
Have you checked the disk integrity?  It's an option on the main menu.

---

### Post by AndyCooll on 2006-04-29
At the partitioning stage did you choose manual install? If so you need to set the name of the partition/mount pointyou are installing to to be called "/" (without the parentheses).

It would be easier however (unless you are trying to dual boot) to simply accept all the defaults, including the partitioning, i.e format whole drive.

:cool:

---

### Post by ComplexNumber on 2006-04-29
you have to set the mount point as '/'. at the very least, you will need 2 partitions - the root(ie '/') partition and the swap partition. the swap partition usually need to be twice the size of your PC's RAM. the swap area is the linux equivelent of window's virtual memory. many people also have a '/home'(this is so that, if you want to install another distro but want to keep your home settings) directory and a '/boot'(most people set the boot area to be the MBR) directory.

---

### Post by HiTmE on 2006-04-29
i did not choose manual install i did the erase the entire disk and use LVM option

---

