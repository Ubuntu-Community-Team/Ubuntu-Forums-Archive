---
title: "USB permissions"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-03-18
My usb flash memory all of a sudden requires me to change its permission  ( I thinks its because I used it on a wndows computer ,,anyway cant read or write to it 

Question 1 

How do I change permissions permenantly, for ALL usb sticks as My Wife has one , I get given file from work in USB form  

I dont want to be giving permissions everytime I hot swap a usb stick !

Have been to wiki ,, but couldnt figure out  for usb sticks 

Stephen

---

### Post by bodhi.zazen on 2007-03-19
Moved to Absolute beginners Talk ~ Hopefully you will get a faster response.

My only thought is remove (unmount and physically remove) all your usb devices.

Delete all referances to usb devices in /media

Perhaps the problem is a residual directory in /media that then is re-used when you plug in new usb devices.

Then re-try your usb devices.

HTH

---

### Post by skot on 2007-03-19
just went through this with my usb external HD.  
if your switching between windows (ntfs) and linux (ext3/fat32) they need to have a common format. 
i have my desktop with has linux running and im currently on my laptop which im helping to diag my problems (hehe) i needed to swap files and codes.

anyways here is what i did which i think confirms your issue.  on my external HD i made a 5GB partition in FAT32 so both system can use it. so if you can make a section that uses fat32, try that. if it is set up as ntfs.

hope this helps. im a total linux beginner and i may not know what im doing.
but form what you siad i had the same problem and it fixed it.

skot

---

### Post by basilwatson on 2007-03-19
Yup it windows that causing the prob.. its ( in particular ) win 2000 .. As I just printed off a file and its koshed that usb disk 

the other one I backed up , formated and its fine again !!!  So ..I think that that laptop is going to Linuxed ,,, 

I only use it for auto cad .... and I prefer a linux version !

Still anythoughts as to why ???

Stephen

---

### Post by floke on 2007-03-19
This might help

[http://ubuntuforums.org/showthread.php?t=387644](http://ubuntuforums.org/showthread.php?t=387644)

---

