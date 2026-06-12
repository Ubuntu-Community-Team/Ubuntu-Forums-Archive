---
title: "Upgrading to Dapper Gone Awry"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by MinkaGrl01 on 2006-06-16
I posted in another thread but got no response so I'm starting my own.

Somehow I did something wrong during my upgrade, I thought I was doing everything right, I went through and did everything through update manager and then after the reboot it tells me that it "failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" after hitting 'enter' it goes to another error window which doesn'tmake much sense to me.

I'm just not sure what I did wrong. But there is now an extra 23 partitions on my hdd with several recovery modes. Hopefully all this is easy to fix but I'm not sure how I screwed it up or how to fix it.

---

### Post by nudnik on 2006-06-16
I cannot address the rest of your issues as I lack the experience to do so, but as far as xserver....you might be able to get it to restart by typing the following after the command prompt:

sudo dpkg-reconfigure -phigh xserver-xorg

Reboot and see what happens. With any luck you will at least have a graphical interface again.

---

### Post by raptros-v76 on 2006-06-16
do you still have network? this sounds like a problem ive dealt with before. you may have completely lost X. this is what you need to do:
go into one of the tty's;
sudo (nano or vim) /etc/apt/sources.list
comment out all of the non official repositories
sudo apt-get update
sudo apt-get dist-upgrade
reboot, see if it works

---

### Post by raptros-v76 on 2006-06-16
if that doesnt work, try 
sudo apt-get install xserver-xorg

---

