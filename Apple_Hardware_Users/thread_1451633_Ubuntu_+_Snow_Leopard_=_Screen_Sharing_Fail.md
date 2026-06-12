---
title: "Ubuntu + Snow Leopard = Screen Sharing Fail"
date: 2010-04-10
forum: Apple Hardware Users
---

### Post by .Nate22 on 2010-04-10
Hey all-
I've had my joys and failures with Ubuntu. To save time-a little background real quickly: my home network uses all 4 major operating systems. XP, 7, Snow, and Ubuntu 9.01. I use Samba on the Ubuntu machine (Dell Dimension 4600) to host shared space for everyone to use. I use CUPS to share a couple of printers over the network. 

What I used to be able to do:
I used to be able to use remote desktop to control the Ubuntu machine from my MacBook Pro when I was running Ubuntu 7.10 on the Ubuntu machine and Leopard (OSX 10.5) on my MacBook Pro. 

What I did:
Thinking I was gonna be super cutting-edge and modern, I decided to "upgrade" my operating systems. If I could go back in time, I would take a 2x4 to that notion. (I had such bad luck with sharing printers in Ubuntu 9.10 that I wiped EVERYTHING and installed a fresh copy of Ubuntu 9.01 to resolve that problem.)  
I reformatted my MacBook Pro and installed Snow Leopard (OSX 10.6.3) on it. 

I enabled screen sharing in Ubuntu as per these instruction:
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

I'm not sure if I installed screen sharing on the Mac, or if it came with the upgrade, but my point is, I have the basic Apple screen sharing program on my mac...The same one that used to work in regular Leopard (OSX 10.5). 


The Problem:
When I go to connect to the Ubuntu machine, I CAN connect, I do see the desktop (if the Ubuntu computer is NOT asleep, otherwise I get a black display).  However, I CANNOT click, type or use my keyboard at all, open programs, etc. Essentially, if you imagine a computer behind a glass display, you can grasp my functionality completely.  You can look, but not touch. It's very annoying.

I've been frustrated by this problem for quite some time. I'm hoping someone out there may be able to help me.  If you have had any such experiences or think you may know a solution, please post below. 

Thank you for reading this.

Cheers,

Nate


*****New Development**********

I found out that I am to click and type using screen sharing. HOWEVER, I cannot see the changes to ANYTHING that would be displayed on the Ubuntu desktop screen on my laptop's screen sharing window.  I can use screen sharing from my Mac laptop to my Ubuntu desktop if I am sitting in the same room as the desktop and can see the Ubuntu desktop's display.  (Completely defeats the purpose of screen sharing)

---

### Post by Tylerjd on 2010-04-10
This is a bug when using Compiz (the effects in your desktop). Disable compiz (**System>Appearance>Visual Effects**) and then click none. This disables Compiz. Then screen Sharing should work 100% like it should.

---

### Post by spoier on 2010-04-13
Thanks!  Disabling Compiz fixed my sharing problem as well (OS X client -> Ubuntu 9.10)

---

