---
title: "is there hope or is it just wasted effort"
date: 2008-11-25
forum: Apple Hardware Users
---

### Post by rebelj12a on 2008-11-25
ok the simple part of it is i want to use test disk to recover my entire drive from before it was reformatted...

testdisk insatlled on ubuntu - use remastersys to create a live cd no problems there

well heres the back story, on my macbook pro i had mac osx as the primary partition and windows set up as a bootcamp partition... there was a problem with the bootcamp partition because i was using it with vmware when i upgrade...it would not boot

so i used the windows boot cd to reinstall windows onto the bootcamp drive.. howeveri deleted my mac partition

wouldnt be a problem but i didnt have a distro of linux with testdisk... (didnt even know about it at the time)

and i had a computer that basically had nothing os i ended up reinstalling mac osx partitioning the drive with bootcamp and installing linux

i did this process more than 3 times... dont ask - i used refit which didnt work for me so i did it again without (first time installing on mac) etc etc

so is there any chance i can use testdisk to recover the original partitions from the hard drive if i boot using the live cd?

i used photorec to recover files but im getting 52 vmdk -vmware disks, multiples of a file i have no idea what it is and far too many duplicates and copies of what im looking for plus it cant recognize the file format of evernote documents which is something else i need... is there any hope or is all lost?

---

### Post by Leslie Viljoen on 2008-11-26
If I understand what you are saying then no, there's no hope. If you want to get parts of the original data back, perhaps some of it is still there, but I very much doubt you'd get more than that, and even that would probably require a data recovery specialist. This is because files are often broken up physically on the disk and you need software that can find and read the directory information and follow the file chains to reconstruct them. This software needs to be filesystem specific. 

By the way, it would be easier to understand you if you put the process you followed in simple point form, and then stated your question, something like this:

1. I had OSX and Windows via bootcamp on my Macbook Pro 
2. The bootcamp partition stopped booting
3. I reinstalled Windows, deleting the OSX partition 
4. I reinstalled OSX
5. I installed Linux
6. I reinstalled Windows, OSX and Linux 2 more times
7. Trying to use photorec to recover, my files look crazy
 
Q: How do I use a Linux live CD to recover the original partitions and data?

---

