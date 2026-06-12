---
title: "amd64 or i386?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by deadgoon on 2006-02-03
I have an AMD Althlon 64 2800+ and I wanted to get some opinions on which version of Ubuntu to use.  Should I use the amd64 port or the i386 port?  I am downloading the amd64 live CD so that I can get a feel for it and to make sure it will work with my hardware.

My main concern with the amd64 port is stability and availablity of packages.  I am planning on using Ubuntu as my primary OS, so I want everything to work out of the box and I'll want everything to be easy to upgrade or install, with a minimum of special hacks.  I guess I'm really asking, is amd64 ready for primetime?  If there is another thread on this topic, please point me to it!

While I'm not new to the linux game, I placed this in the New section because I'm sure others are looking for similar information.  I used Suse as my primary OS for about 6 months, but that was about 3 or 4 years ago and I've been in the Windows or Mac world since that time.

Here are some hardware specs from my machine in case that might help.

Athlon 64 2800+
1GB RAM
200GB SATA HDD
CD-RW/DVD-ROM IDE
Floppy
Nvidia Geforce FX 5500 graphics card
Nvidia nForce3 250 chipset

---

### Post by rooster on 2006-02-03
As for me I believe that at the moment the more development gets into the i386 programs. The AMD64 is working, but you can't get everything that is working under i386.

So maybe you can build a dual boot with 64 and 32 bit? So you can check for yourself if everything is working in AMD64. You can use a seperate /home partition, so your files can be shared (don't know exactly if this is working in all cases, but in theory it should).

But maybe there is someone else who has tested it before?

Roster

---

### Post by Perfect Storm on 2006-02-03
Roosters Idea is good. But if you have to choose one I'll go for i386.

---

### Post by Denis on 2006-02-03
Hi

I had to make that decision too. I chose to install the i386 version. 

As far as I know the most importent difference is that some things are not yet available, or require a special trick in Ubuntu amd64. 
The flash player and the win32 codecs (like divx and wmp codec) are such items. 
you can check out the [amd 64 bit support forum]("http://ubuntuforums.org/forumdisplay.php?f=96") to get some more information about that. Maybe that will help you with making the choice. 

Concerning the default packages, you won't encounter any problem with those. As far as I know the default packages as well as all the other programs you get with synaptic should work perfectly with amd64. (Those packages are not compiled for a specific procesor.)

Stability shouldn't be a problem either. The amd64 version should be as stable as the others. 

If those codecs and the flash player are no problem for you, you can go with amd64 I guess. For more specific information I suggest you take a look in the amd64 forum. 

I chose to not use the amd64 version because I do need those codecs e.g. I didn't want to make ik more complex for me than it already is. When everything is supported in amd64 Ubuntu I may want to swich too. 

The decision is up to you of cource. Also remember that the amd64 version won't be *that* much faster. I'm pretty sure you won't notice when you don't run specific processor intensive programs.

---

### Post by Perfect Storm on 2006-02-03
Just a note, if you choose i386 you might afterwards change kernel to k7 as i386 don't support 1g memory and also getting the nvidia drivers :)

---

### Post by deadgoon on 2006-02-03
Thanks to everyone for their quick and informative answers.  I think I'll stick with the i386 for now as it seems to meet more of my requirements for "working out of the box."  Now I just have to pick between Ubuntu and Kubuntu.  <insert flamewar here> :-)

Actually, I'm going to install Ubuntu, then apt-get the Kubuntu packages and have the best of both worlds!  BTW: I'm posting this from the Kubuntu live CD.

---

### Post by anindya_m on 2006-08-21
Hello. It should be possible to install AMD64 and still run 32 bit programs. For example I have two installations of Firefox. The 32 bit version supports all plugins. However, the plugins won't work with the 64-bit version of Firefox.

---

### Post by huygens on 2006-08-21
> **deadgoon said:**
> is amd64 ready for primetime?
 
Yes and no. I have installed Ubuntu 64 on a Sempron (which had also 64bit instruction). It works flawlesly out of the box. But once you want to use a few proprietary software, you get the problem to find proper 64bit applications. So for peace of mind and point-and-click installation of software, I went back to the 32bit version of Ubuntu.
 
> **Artificial Intelligence said:**
> Just a note, if you choose i386 you might afterwards change kernel to k7 as i386 don't support 1g memory and also getting the nvidia drivers :)

I do not know for nvidia's driver, but for sure you can use the default kernel (i386) with 1GB of RAM. This is the configuration of my two computers, and Ubuntu with an i386 kernel is able to use my 1GB of RAM without a problem.

> **deadgoon said:**
> Now I just have to pick between Ubuntu and Kubuntu. 

I did not try Kubuntu 6.06. But for what concern the previous version 5.10, I had installed Kubuntu first (as I tend to prefer KDE over Gnome), but I was quite disappointed as the configuration GUI were not as mature as the one available on Ubuntu. So I switched to Ubuntu with Gnome as I want also a system working out-of-the-box. But nonetheless, Kubuntu 5.10 was a great product, and it was handling bluetooth connectivity better than Ubuntu 6.06 in my opinion (the KDE tools are really userfriendly in this matter)...
So perhaps, try Kubuntu and Ubuntu from the Live CD, and make up your own opinion :) It's hard to choose...

Huygens

---

### Post by Kilz on 2006-08-21
I think that everyone is welcome to their opinion. But posting this question here is going to get a different set of response's than if someone had posted in the [64bit user section.]("http://www.ubuntuforums.org/forumdisplay.php?f=134")
You now have a few response's from people who failed to install 64bit, or who run 32bit. I run 64bit. I am also very active on the 64bit section helping people.
First I will shoot down some FUD
1)There is only a 2% deference in packages between the AMD64 version and the i386 according to launchpad. This includes applications and libraries. I have both versions running on my network and cant for the life of me find anything that is missing. Its possible that there are some ancient applications not ported, or that libraries were merged or not needed.
2) A quick look at my signature reveals that there are howto's/automatic install scripts for the 2 things most people are claiming are missing. Wine and firefox with plugins.
3) The 64bit OS is faster, if only slightly in some cases. In others there is a 30% increase. Things like encoding media when you rip something. 3d modeling, compiling, and other number crunching activities.
4) In some cases there are real problems running a 32bit OS on a 64bit system. Reports of crashes, application crashes, slow operation on 32bit. These problems vanished when a 64bit os was installed.

Are there problems? Yes, but there are problems with installing a 32bit os. Nothing is perfect. Will you have to spend a little more time setting up? Maybe. It depends on what applications you run. For most common applications NO.
There are advantages and disadvantages. But don't pick a os version because someone who failed to set it up, or doesn't run it tells you to.
I wish the helpfull people in this forum would direct people with 64bits systems to the 64bit section when this question is asked.

---

