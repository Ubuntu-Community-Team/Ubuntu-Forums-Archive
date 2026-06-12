---
title: "Grub 1.5 multiple errors."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by thach562 on 2008-01-15
Hello, 
This is my first time using Ubuntu 7.10 and I kinda messed up...bad. 
I was dual booting vista/ubuntu perfect until I messed around with some settings in ubuntu regarding resolution/screen size and then it went all poopoo on me. Then doing the idiotic thing, I reinstalled ubunto by booting into the live cd, deleteing the ex3 (I think? Not sure) partition and the /swap partition. I installed it (I guess into the new partition) and I thought everything was fine until I try to boot up my computer. Now I GRUB gives me an error 15 or error 17 or error 22. I know the error lies in stage 1 of grub. 

I have tried using super grub to try and auto fix it but it doesn't work. 
I been looking around on the forums for about 2 days and some solutions that I already looked at and tried are 

Going into my bios to see if my hd was recognized. 
Using Super Grub

I have these set of commands to reinstall grub using in a terminal. 
sudo grub 
find /boot/grub/stage1
roof (hd0,1)
setup (hd0)

the problem is I don't know any programing command to get me into a terminal except for the one located when I boot up with the live cd. 


Kinda lost and kinda at the end of my rope. 

thanks.

---

### Post by thach562 on 2008-01-15
I guess to add a little more. 
I opened a terminal using the live cd and typed in 
sudo grub
grub>find /boot/grub/stage1 
and it returns with 
Error 15: File not found. 



no idea what that means. 
/cry

---

