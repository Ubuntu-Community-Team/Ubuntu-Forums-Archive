---
title: "Triple boot"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by eikichi on 2009-11-08
Hi there,

I am planning to set up a triple boot on macbook 5,1.

I want to be able to boot Kubuntu, win 7 and osx. 

My question is quite trivial and I am just wondering if it is the right way to go about it..

So, I am thinking to first create two extra partitions, one for win7 and one for kubuntu.

I should first install windows7 using bootcamp which is the easy part, no need for refit or any of the like.

Now this is the part which confuses me the most and I've never read in any similar articles, should I use the wubi installer to install Kubuntu from within windows 7 or not? And if i do and I am successful will I need refit?

Regards,
Eikichi

---

### Post by techevo on 2009-11-09
when i triple booted my mac, in used boot camp like you have said.

then installed refit

made the ubuntu martition using disk utility (installed on mac already)
also make a swap area if you want (should be the same size as your physical memory)

install ubuntu, but when you get to the last screen of the install, cliuck advanced and install the bootloader ie grub to the partition where ubuntu is installed.
 
sda4 or somethinbg it will be.

now boot up into mac, then windows, then ubuntu to chewck they all work.

NOTE: If windows blue screens while booting up, you will need to go into linux, mount the windows partition and change the boot.ini file to read from the correwct partion.

although if you followed the instructions then you should be fine.

good luck :)

techevo

---

