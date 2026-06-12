---
title: "Home server reality check"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by snakelock on 2008-01-19
Hi Folks,

My plan is to build a new machine with Foxconn MB build in Gigabit LAN, Celeron Processor and 1 GB RAM as a glorified NAS.  Initially it will have two or three of my 200 GB HDDs for storage (Data, Music+++and Video later) a new 750 GB HDD as a backup drive.  I also wish to plug my HP PSC 1315 All-in-One printer into the machine.  I have a network with three Win XP Pro machines and two wireless routers (one degraded as simple wireless access point).  I want to use Ubuntu Server and Samba.  Knowledge about command line dates back from DOS and is very, very rusty, but I am happy to learn.  Yes, I do understand and expect Ubuntu is not Windows.
Once everything is up and running I want to put the machine somewhere in the corner and let it run.  Backup should happen automatically and I should be able to shut down, wakeup and maintain the computer remotely from my Windows XP machines.  So save electricity the mains switch will be off at night and when not at home.  
Are my goals realistic?
The next step, once a feel more confident with Linux, is to build a Linux multimedia server and connect it to my HiFi/home cinema.
Many thanks for your answers.

Snakelock

---

### Post by gn2 on 2008-01-19
Have you considered just buying a Linksys NSLU2 ?

---

### Post by VidiotGeek on 2008-01-19
I haven't got any real advice to offer you, but it sounds like an awesome project. I'd love to hear how it 
turns out. As for integrating the box with your home theater, the only thing I know of for that goal is using MythTV. I 
know it does the backend server stuff as well as the frontend. I think you have to have another machine for the client 
in the home theater to access it if the box you're building is to be banished to a corner or closet to do it's 
glorified NAS job. I don't have any spare boxes to play around with to attempt any of this stuff so I can only imagine 
how I would go about it, haha.

---

### Post by JoshuaRL on 2008-01-19
You might just be able to find a thin client machine on ebay for cheap, and put Mythbuntu on it.  Depending on how thin it is, you might download the server version and just put the few programs you need on it.

---

### Post by Thund3rstruck on 2008-01-20
The samba server project is going to be much easier than your media center project if you're new to Linux. I have played around with various media center projects and none of them turned out how I expected and they all cost me a lot of time and money. Ultimately I ended up standing up a 2TB NAS server and an old XBOX running XBOX Media Center, which  I'm 100% satisfied with. 

As for your samba server, that one's very simple and there are hundreds of guides for it. Basically you just install samba, create samba users, and edit the smb.conf file. Auto backups are done by making cron jobs and rsync. Remote desktop is built into the OS and terminal access is available remotely through SSH (secure) or telnet (in-secure)

---

### Post by snakelock on 2008-01-20
Thanks a lot

The Samba server will come first to get a feel for Linux. I will also try to keep the power consumption as low as possible.

---

