---
title: "Graphical issues or drivers not fully working?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Zxar on 2008-03-22
I'm pretty new to linux. I've tried to install other linux operating systems, Red Hat Linux for one, but they wouldn't install on the HDD I had. Ubuntu, on the other hand, installed fine and I was able to get up and running. I've searched the forums, here and many other places, for people with some kind of problem as to mine. But even after doing them, or attempting to finish them with problems, I have reached the end of my linux code, and understanding, dictionary.

I have an ATI x1650 Pro PCI-Express Graphics card. Which I already found out the drivers have issues with the linux operating system. But I finally got to a point where I was actually able to boot up into main GUI without having Ubuntu telling me that the drivers are messed up, and the display was set to low res. 

So, I have Ubuntu being able to run with the ATI drivers, kind of, but I can obviously tell things are going at top knotch. Since the you can see lines running across the monitor when it's displaying anything, and loading windows or programs is severly choppy/laggy. I would think, from using windows all my life, that it's the refresh rate not being fast enough.

I have already reinstalled multiple times trying different methods of getting the GUI to work properly and this is the first test of actually getting somewhere. So, if anyone has any ideas of what I can do, or not too would be more the case, to redo any of the steps I took to get here, then I am all ears, well eyes since I can't hear anyone through a forum.

Here is what I did to get to where I am at from a fresh install of Ubuntu Gutsy 7.10 install.

I got the drivers off the ATI website for my video card.

I grabbed the linux drivers for my video card model. (only problem is there is two versions of linux drivers so I grabbed them both. Just in case)

They were both .run files. So, I had to surf the net on what to do to run them. (which I learned the executible checkbox in properties wasn't check and so I checked it)

I ran the file using sudo /home/zxar/Desktop/filenamehere.run and input my password to allow the install to commence.

Upon finishing the install I rebooted and then downloaded all the updates available for Gutsy using the terminal. sudo apt-get upgrade

Rebooted after the updates have completed. (everything still working fine but couldn't activate the visual effects or anything of the sort)

After the reboot opened the terminal and used sudo apt-get install xserver-xgl (have no idea what this is but everyone says you needed it for something. So I grabbed it)

Rebooted again and still nothing changed, so I installed the restricted drivers for the ATI Radeon Card and did another Reboot.

Apparently Ubuntu didn't like that idea and that's when I started having the problems. So I was experementing with the Screens and Graphics settings, changing the drivers supposedly being used and rebooting, but to no avail with any of them.

If anyone has any suggestions at all I'll gladly try them. Cause I know how to get back to the point where Gutsy was in a semi-working condition. Haha. I won't be able to try out the ideas till later tomarrow since easter and being my 21st b-day I'll be away from my tower that has Gutsy on the partitioned HDD. But the time away will give me more time to think about things I could do, and ways to improve on the matter and any feedback would be a great help.

For additional specs for my computer specs running Gutsy
40G Seagate HDD ST340810A (Model)
ATI Radeon x1650 Pro PCI-E (previously stated)
1x1024MB DDR2 RAM DIMM 433 [if I remember correctly] (Kingston)
AMD Athlon 64 X2 Dual-Core 2.61Ghz 1Mb cache
KDS Visual Sensations 7i CRT Monitor.

Thanks for any/all replies and suggestions.
Zxar

P.s. I tried to add as much detail to my problem as possible. Since me being very new to the Linux scene I know how a small detail can ruin something. *windows programming experience talking* Thanks again.

:Edit: I was wondering, why is it Nvidia is a better graphics card for Linux than ATI? I know ATI works with third parties so they say they can't release source code for thier drivers. Is that the only reason why, or is there something more to it?

---

### Post by c-ron on 2008-03-26
Hey Dude. Glad to see you're checking out Ubuntu. Have you tried the Envy program to install the ATI drivers?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

