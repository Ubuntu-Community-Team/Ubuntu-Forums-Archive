---
title: "Dual Boot and other NewB issues"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by heyz on 2006-08-13
Hi

I am asking this cos the help.ubuntu.com site seems to be down.
I wanna know how i can install ubuntu with winxp. I have XP64 installed on one drive. I downloaded the AMD64 Ubuntu ISO. I went through the installation process, then the partition step came up and I got nervous. Like i cud choose a drive in XP installation I can't do that in Ubuntu. (My first exp with linux installation). So it started taking free space from a drive. And i got nervous. I aborted the installation, booted with XP and came here for help. Just let me know if am doing ok. Can i just install Ubuntu the way I am now. Can i just make a single drive, say, Drive M - 20 GB,  and install ubuntu there? Am i asking too many questions? Why doesnt the help site work?

---

### Post by xpod on 2006-08-13
If your planning on putting ubunto on same drive as xp remember to defrag your xp first and back up all important data.

Also i believe the x86 version of ubunto is a lot less hassle in the long run...

Somebody will correct me if im wrong

---

### Post by masnevets on 2006-08-13
Are you saying you have two harddrives and want Windows on one and Ubuntu on the other? If so, you should be able to select which harddrive you're working on (when you select manually edit partition table) in the top-right corner of the GParted window.

Hope that helps.

---

### Post by xpod on 2006-08-13
Soory i just realised you seem to mabey be talking about two drives in which case you can quite safely select your slave to install ubunto(if thats what your asking)

Thats what i did with 2 drives and it all dual boots fine

edit:Ps I just selected the drive to install and it was all done for me without having to manually make the parttitions ,you can do it yourself though  if you so wish

---

### Post by heyz on 2006-08-13
I havent explained myself properly, my apologies

I have 3 Hard Drives

1) 20 GB Samsung (ATA)
2) 80 GB Seagate (ATA)
3) 250 GB Hitachi SATA II

Each of these have partitions within them.
My idea was to install Ubuntu in one of the partitions of the 3rd Hard Disk. I had made 4 partitions in it. One of the 4 partitions already has XP. Other partitions have stuff - movies n stuff. I wanted to install Ubu in one partition of the 3rd HDD which had no files.

---

### Post by xpod on 2006-08-13
Check with the BIG boys but i think it`s the same procedure.

Start the installer,choose all your keyboard and country options then when it gets to asking you which hd you want to install on choose the hd with your awaiting space and then choose the space in question and you can either manually make the ubunto partitons or you can choose to allow Gparted to do it for you

Thats how i remember it with my slave hd BUT check with somebody more qualified than me first.

Im not sure if sata hds are any different in that regard but i let gparted do all the dirty work for me and it set up the dualboot up with XP without a hitch

---

### Post by Jjohn on 2006-08-13
Hi Heyz,
 Just to add to your confusion I installed the amd 64 distro and had ALL sorts of problems with it. In the finish I installed the 386distro and have now got a lot more functionality

---

### Post by xpod on 2006-08-13
Yeah..THATS what i said too.

I have an athlon amd 64 system but use the 386 distro due to the many problems that seem to occur after install.

Things need a lot more configuring and it`s supposed to be a right royal pain in the butt.

Luckily i HAD`nt  realised this at first and i ended up with 386.

IF i had read more i might have ended up with the "correct" version AND a lot more hassles than i have already.

Confusing eh......THATS the advice we all seeem to get though....UNLESS your a whizz then you can configure anything you want eh...lol

---

### Post by masnevets on 2006-08-13
Okay, then since you have the partitions already set up on your third harddrive, I think what you should be doing is selecting the option that lets you manually edit your partition table. I'm not really familiar with the other options that automate the partition process. But anyway, when it takes you to the table, you can just hit OK since it's all setup, and then the installer will ask where you want root to be and where you want your swap space to be. Since you have one partition for Linux, you'll want it to be an extended one so that you can put additional partitions inside of it (namely one for root and one for swap). 

Also not necessary, but I recommend making a third partition for your /home directory, so that in the future, should you need to reinstall Ubuntu or do a fresh upgrade for Edgy or whatever, you don't need to worry about your personal files/configuration settings. The installer will ask if where you want /home.

I can understand the automated partitioning tool making you nervous (it would make me nervous), so hopefully selecting the manual partition option gives you what you need.

-Steven

---

### Post by xpod on 2006-08-13
I think it must have made me nervous too as i ended up installing on a tiny 3.2g slave hd i took out an even older pc,rather than stealing 10 or 20g off my master drive(scary at the time)

I still let it do it automatically though but i would probably use the manual method NOW seeing as i understand a bit more about partitions.

Especially the separate "home".

My master is fat32 so i can quite easily use it when i run out of space on this wee thing but im still not sure if Ubunto will go and use it automatically when the time comes??

Ive created an ubunto folder in XP but WHAT will happen when all the regular updates finally eats the gig or so left on it`s own hd??

---

