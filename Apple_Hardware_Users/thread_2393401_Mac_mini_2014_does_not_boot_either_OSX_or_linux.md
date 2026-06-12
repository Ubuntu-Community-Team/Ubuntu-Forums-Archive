---
title: "Mac mini 2014 does not boot either OSX or linux"
date: 2018-06-03
forum: Apple Hardware Users
---

### Post by robertarnold659 on 2018-06-03
Hello everyone and thank you for taking the time to read this.

First off, I am new to linux and don't actually know a lot about it. I figured I would give Ubuntu a try to get more familiar with the OS. Im pretty tech savvy and understand the concepts quickly. 

About my problem. I was installing Ubuntu on my Mac mini and used the rEFInd boot in order to have a dual boot going. I set up linux with marginal success and started reading more about applying some fixes that needed to be done a.k.a. drivers and updates. I switched to the efibootmgr (because linux made itself the master boot and the rEFInd screen wouldn't show on boot) and I changed Ubuntu to secondary and then got back into my Mac OS. However, the rEFInd screen did not pop up like it had before. I took note of this and continued logging into OSX to do some work. I came back to ubuntu a little while after and I then started taking a look at the grub menu (I didn't change any thing in it, honestly dont know anything about it so I decided to leave it alone). I also looked at terminal commands with the man *command* technique to learn more to see if there was a way to allow Ubuntu to take over the operations of the dual boot screen. After I had done some research and consideration, I decided to install rEFInd for Ubuntu since I wasn't getting the rEFInd screen through OSX anymore. I then restarted my computer to switch back over to see if had work. All I got was a black screen.

I have tried all the Apple boot commands many times and nothing seems to work. with no results I tried seeing if I could get the Ubuntu loader going using other commands. No such luck their either. Then I tried creating recovery disks, which had no effect either. The Mac mini does chime when starting, but its almost like there is not boot sequence happening. Im just wondering if anyone has any information that could help. 

Thank you for your time. I really appreciate it.

---

### Post by robertarnold659 on 2018-06-10
I figured it out. For those who experience the same problem. You need an additional keyboard and hold the option key during reboot. This is kind of hard to time right, but if you are able to it will bring you to the standard Mac boot manager and you can select the macOS from there.

---

