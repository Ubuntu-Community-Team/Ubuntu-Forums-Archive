---
title: "Programmer new to Linux"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by dwshard on 2006-12-06
Hello,
     I am a .NET programmer and have recently installed Ubuntu on my machine.  Aside from a dual screen issue and a grub pointing to the wrong place thing (which I am hoping to resolve soon) everything is going very well.  It has been about a week and I am not attempting to become productive with my new computer.  I have installed Mono develop which work very well for making console programs but doesn't seem to much for ASP.NET stuff.  Does anyone know of an IDE for this or should I just try to use #Develop/wine.  Or maybe there is some kind of resource that is out there that I can use to find more out.  Thanks for any information.

---

### Post by thejerryguy on 2006-12-06
i just started with Ubuntu. A friend told me to check out the following site for info on using visual studio with mono. Does this help any. I hope to do .net type programming on my desktop machin also.

[http://tirania.org/blog/archive/2006/Feb-25.html](http://tirania.org/blog/archive/2006/Feb-25.html)

---

### Post by dwshard on 2006-12-06
Thanks for the link, I think thats going to be a good start.  Now does anyone know of a way to get monodevelop to do ASP.NET.  Or am I just spinning my wheels and I should just use PHP.  I already have about 300 sites developed in c# and VB usng asp.net 2.0 and 1.1 and i would like to continue using the same development tools for all my systems.  This VS link will do good (until I want to switch to ubuntu on my desktop.  It turns out that ubuntu server performs very well with the execution/hosting of asp.net apps.  i am interested in seeing how it compares to MS server core.

---

### Post by Atomic Dog on 2006-12-06
You should check out the mono project [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)  It is not as slick as the .net env but they are getting better.

They have a vmware image you can download.  Get vmware player and you can give it a shot without.

Also I highly recommend you get automatix2, it will install all the good stuff without the pain.

---

### Post by pmasiar on 2006-12-06
Let me say first I have no idea if Mono implements 90%, 99% or 100% of .NET (and which .NET we are talking about: 1.0? 2.0? 3.0?). Linux and .NET are competing platforms, no way around it. Incompatibility between versions is inevitable. If you want to learn and handle this, it might be very valuable expertise to know. Not many people are willing to do that, I guess.

But another approach is possible. Microsoft just released IronPython (under GPL!), which is .NET reimplementation of Python. IronPython uses different (.NET) libraries and is not 100% CPython yet (and might never be), but Python is (unlike C#) designed as multiplatform language, and is icredibly flexible and productive. IronPython is the only scripting language with command shell for .NET. Try it once and compare with static typed languages like C#. You will feel the freedom!

With python, maybe you can get hired by Google :-)

---

### Post by nickburns on 2006-12-06
Not to be a grumpy butt about Mono, but it (Mono) is no where ready for comparison to .net.  They have implemented the 1.4 framework only and the IDE needs some serious work.  You may want to use vmware for windows development and Ubuntu for your main OS. I know many people do this to get the best of both worlds.

---

### Post by dwshard on 2006-12-07
I am going to sound really dumb, I never thought of using VMware for development.  I use it for administering my Linux servers (ssh -X works so much better than through Cygwin), basically I never thought of running windows on Ubuntu.  

Also along a different line i was thinking of using mono for only command prompt scheduled tasks but i could see myself switching to python for this.  After messing around with it last night I went from never using it to writing a file downloader in like 2 hours.  It seems like one of those things you could just keep open on your desktop to solve those quick "I wonder if I could do this..." type problems.

---

### Post by nickburns on 2006-12-07
Use this great howto to get vmware installed on Ubuntu

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by dwshard on 2006-12-07
Great How-to you really can get the best of both worlds and not too much slower than running natively (although 3 gigs of ram does help :) )

---

### Post by nickburns on 2006-12-07
The new vmware will allow you to 'grow' your HD space for the vmwareOS as needed, you can specify a max size (lets say 10 gig) and you install windows and the HD file for vmware is only 1.5 gigs, then as you add programs, like .net the file will continue to grow.

It sounds like you have a nice enough system to easily run vmware on top of Ubuntu.

---

### Post by dwshard on 2006-12-08
I am all setup.  It is working really well.  The nice thing about it that I can back up my work on the Ubuntu part of the machine and rebuild XP when it gets screwed up.  it is kind of funny to think that i am using samba and ftp to transfer files around on my hard drive.

---

### Post by nickburns on 2006-12-08
I am a programmer too, and I have a 'clean' install of XP that I keep in a backup folder.  Every few months when XP gets slow and dirty, I just copy it back over to vmware folder and start fresh in minutes.

To transfer file I have used PUTTY on my windows side to SFTP into linux, it is still the same as Samba, I guess.  I am working on getting rsync to work on windows and linux together, I think Cygwin will play nice with a bit of help.

---

### Post by dwshard on 2006-12-11
That is a really good idea.  I use ghosting on my "real" xp machine for the same purpose just make all your profiles and info on a second drive.

---

