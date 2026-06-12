---
title: "Considering dual booting Ubuntu on a Mac"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by NerdHerd628 on 2007-11-22
Hello forum,

I am the paradigm of a linux noob.  As of this posting I have never used a linux platform, but I hear such cool things that I want to jump in and give it a try.

Right now I own a ca. 2004, 1**4" iBook G4 1GHz with 640 MB of RAM**.  I rely on my Mac for work and school so I don't want to jeopardize messing up my only working computer.

What I would love to do is set up my Mac to dual-boot ubuntu, probably from an external HD if possible.

Now I have no clue how to do this, or even if it is possible or a good idea to do so.

I just wanna reiterate that I am very new to linux, so where should I start? What things should I learn?  I am not nervous about learning to use the command line and I would be willing to learn whatever possible.

Any advice?

Thanks all.

---

### Post by kaklehona on 2007-11-23
I have little experience with mac, let alone dualbooting it, but I guess it could be done. I have dual boot on my laptop, and it was not all that hard to do, but I recommend taking backup of all important data before you start trying things out. 

I usually test with what is called a live cd/dvd before installing things. That is a linux version that runs from the cd without installing on your machine (at least that's how I understood it). If you decide to have dual boot, the most important thing for you would to learn how to repartition your mac without destroying what's on it. I have done it with several computers, and I guess tools for mac are available as well. Another thing that it is good to know a little about is Grub, the thing that makes you able to chose what OS to load. I am sure you will learn linux as you go along and start using it, that's the way I am doing it. You might read a little about unix thought, maybe something like this tutorial would be good:

[http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html](http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html)

I think most unix commands work on mac as well. Try opening a terminal window and testing the different things that are mentioned in the tutorial!

---

### Post by mike555 on 2007-11-23
Both my Mac's dual boot, My IMac is what I'm using now, I cloned my harddrive onto a firewire ext. harddrive , then partitioned it into three different size partitions ,using the disc utility , one for Mac, one for Linux , and a small one for swap (two GB in my case) , restarted, then cloned it back to the first partition ,restarted the Mac and  installed " refit " on it, then put in the Alt Ubuntu CD   and installed to the other partition (using the manual setting and formating the partition I made for Ubuntu and setting it as "  /  " and formatting the small partition as " Linux swap " , then install ............ restart and you should have a choice of booting into Mac or Linux ......   in Linux you may need to install the video drivers ...

---

### Post by mike555 on 2007-11-23
Oh, sorry , I see you have a PPC based G4 .... so I don't think refit will work ........ I understand there are PPC based Ubuntu CDs , you might just try them (without Refit) ....... but be sure to backup (clone) your harddrive onto a firewire ext. drive first, just in case .........   
  also you might check out the Mac forum area .

---

### Post by neoguy2012 on 2007-11-23
Hi, I'm not too experienced with macs, but on the off-chance that you just want to run some linux programs... they might be available on macs as well through fink or macports.

[http://finkproject.org/](http://finkproject.org/)
[http://www.macports.org/](http://www.macports.org/)

Although having linux on the machine is nice as well...

---

