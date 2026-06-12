---
title: "How to access to a device with Windows CE??"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-28
Hi, 

I got a device with Windows CE installed. I'm wondering how I can access to it via ubuntu 7.10.

---

### Post by richarglamb on 2008-01-28
What type of device is it? - and what you would want to access?

---

### Post by taekr on 2008-01-28
> **richarglamb said:**
> What type of device is it? - and what you would want to access?

I just bought a PMP (portable Media Player). [http://www.mobilewhack.com/maxian-e900-pmp-for-korea/](http://www.mobilewhack.com/maxian-e900-pmp-for-korea/)

A problem I have is when I connect the player (WindowsCE installed), Ubuntu can recognise the player but only in read-only mode. I can't copy stuffs into the player. 

It's not a mounting problem. I did..  (File system is FAT32)

#1 
Unmount the folder (PMP)
sudo mkdir /media/test
sudo mount /dev/sdc1 /media/test -t vfat -o umask=000

#2 
sudo mount -t vfat -w /dev/hda1 /media/test

#3 
sudo nautilus 

But all doesn't work. 

I have uploaded two screenshots. you will see that there are a lot files with funny letters. I don't see them in XP in 1.png

in 2.png, I ran sudo nautilus but there is still a lock icon on PMP folder. 


Help me!

---

