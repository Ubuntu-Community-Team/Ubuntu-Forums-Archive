---
title: "New Noob to linux"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Parms on 2007-08-19
OK, I have browsed some forums and I am looking for more specific answers. I have a HP pavilion dv8000 with the AMD 64bit. 1.8 ghz with 1 gig ram. 

MY first question is which version to download?
7.04
6.06  
What exactly is the difference? Just the support Dates? 

I want to run the add-on "Beryl" I think it is that has that vista type feel to it.

I have 2 -  80gig hard drives, and want ubuntu on my second hard drive. Keeping everything on my 1st hard drive there.

Another thing I want to do is have a boot loader start when my computer is turned on. So I may select what OS to load. Don't know if this is a problem but I messed with the boot screen to show a picture instead of the windows image. Don't remember how or why I even messed with it. It was a long time ago. But I have the option of picking my picture or the windows default boot.ini. Don't know how to correct this without messing up my computer. I guess windows won't load if the boot.ini is messed up.

These are basically the things I need to know before I start. I don't need a guide to install or anything. I just want to keep my windows OS and install unbuntu on my secondary drive.

---

### Post by Ozeuss on 2007-08-19
> **Parms said:**
> 
MY first question is which version to download?
7.04
6.06  
What exactly is the difference? Just the support Dates? 
I want to run the add-on "Beryl" I think it is that has that vista type feel to it.
I have 2 -  80gig hard drives, and want ubuntu on my second hard drive. Keeping everything on my 1st hard drive there.
Another thing I want to do is have a boot loader start when my computer is turned on. So I may select what OS to load. Don't know if this is a problem but I messed with the boot screen to show a picture instead of the windows image. Don't remember how or why I even messed with it. It was a long time ago. But I have the option of picking my picture or the windows default boot.ini. Don't know how to correct this without messing up my computer. I guess windows won't load if the boot.ini is messed up.
These are basically the things I need to know before I start. I don't need a guide to install or anything. I just want to keep my windows OS and install unbuntu on my secondary drive.
You probably would enjoy feisty better. the difference that feisty (7.04) contains newer packages and a bit more funcitonality, while dapper is more stable.
in Feisty, there's "desktop effects" that give you some of the effects you want. note that beryl re-merged with compiz and now its called compiz.
ubuntu installs a boot loader (called grub) by default, and it gives you a menu that enbale you to choose an OS. maybe you should try to fix the windows boot.ini. you should be able to do that with a windows-install cd, and typing the 'fixmbr' command.
just make sure that your computer boots from the hardrive you had grub installed to.

---

### Post by Parms on 2007-08-19
OK, thank you. I started my downlao9d, should be done in about 45min. Plus 2 minutes to burn ISO. I've started to look into fixing my boot.ini file. I have the original I think I just need to find out where I placed the boot loader program I used, to correct it. 

OK, the plan is to get the disc ready. Then I plan to boot my computer and change the bios to boot from disc, then I can install on 2nd hard drive. Then when finished I can change the boot order, to start the 2nd hard drive. So when I reboot after that the GRUB will be the boot loader? So I can pick which OS to run, or do I have to change the bios every time?  

Thanks in advance.

Trying to learn quick so I can start geeking around with it. I tried fedora core before, but never got the boot loader to work right. (different computer)

---

### Post by hyper_ch on 2007-08-19
burn the iso as slow as possible...

Google for "psychocat ubuntu". That website has a lot of beginners infos and a lot of your questions should be answereed there...

---

### Post by Ozeuss on 2007-08-19
if your wondering about dual booting, you can check out [aysiu's instructions]("http://www.psychocats.net/ubuntu/installing") as the previous post recommended.
if you want to be comprehensive about installing a boot loader, you can check out [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") and [this page]("http://users.bigpond.net.au/hermanzone/p6.htm")
but don't get overwhelmed by it.

in general, the install process is automated, and ubuntu will suppose to identify windows and know where to install the boot loader, so i think you won't need to change the boot sequence of the disks.

---

