---
title: "Everything about Arch..please help."
date: 2009-01-31
forum: Arch and derivatives
---

### Post by diwas on 2009-01-31
Ubuntu was my first Linux distro. Now i want to use Arch. I've heard that in Arch one needs to configure everything.
1. Is Arch available with KDE 4.2? I want to install the latest Arch version, where can I do that?

2. I have two hard drives, one is ATA (primary) other one is SATA (secondary). I dont have any free space in ATA drive, so is it possible to install in SATA? I hope I dont have to change anything in the BIOS to do that. (BTW now I have Win XP and Ubuntu Ibex dual boot, I wish to make triple boot with Arch.)

3. Is it possible to install Arch in virtual environment? Like either inside XP or Ubuntu? If yes, is the installation same like a fresh hard drive partitioned install? 

These questions might be naive, but I wish to use Arch. 

Thank you

---

### Post by binbash on 2009-01-31
3- with virtual machine
1-yes , easiest way to install : [http://chakra-project.org/download-iso.html](http://chakra-project.org/download-iso.html)
2- Probably yes since i didn't try that

---

### Post by der_joachim on 2009-01-31
If you would like to know whether Arch is something you like, I suggest reading [the Arch way](http://wiki.archlinux.org/index.php/The_Arch_Way). 

As for your questions:
1) KDE 4.2 is [available](http://wiki.archlinux.org/index.php/Kde) in Arch.
2) It depends on the boot loader you would like to use. AFAIK, arch supports any boot loader, so you'll just have to decide which one you want to use.
3) On the arch forums I read a thread about a user who had an experimental arch setup running within his regular arch installation, so I think that that answers your question. The few times that I actually saw a virtual machine run, was on a large file which contained all partitions of the VM.

[Edit] Darn, binbash beat me to it. :)

---

### Post by diwas on 2009-01-31
What are the disadvantages (if any) of using Arch in virtual over normal install?

---

### Post by gjoellee on 2009-01-31
> **diwas said:**
> Ubuntu was my first Linux distro. Now i want to use Arch. I've heard that in Arch one needs to configure everything.
1. Is Arch available with KDE 4.2? I want to install the latest Arch version, where can I do that?

3. Is it possible to install Arch in virtual environment? Like either inside XP or Ubuntu? If yes, is the installation same like a fresh hard drive partitioned install? 

These questions might be naive, but I wish to use Arch. 

Thank you

1. Yes, KDE 4.2 was in Arch before it was officially released

3. Yes that is possible, you might get some bugs from the virtual machine though

TIP: [www.archux.com](www.archux.com) will help you on the way

---

### Post by smartboyathome on 2009-01-31
> **diwas said:**
> What are the disadvantages (if any) of using Arch in virtual over normal install?

Speed, mainly. Also, you can't use 3D stuff unless you use Virtualbox (which has poor performance and only does OpenGL). It may have bugs related to the virtual machine as well (stated above).

---

### Post by diwas on 2009-01-31
Then I guess installing Arch in fresh partition would be good. 
I hope I dont ruin everything (I am actually nervous hehehehe)

---

### Post by smartboyathome on 2009-01-31
> **diwas said:**
> Then I guess installing Arch in fresh partition would be good. 
I hope I dont ruin everything (I am actually nervous hehehehe)

Just follow the [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") and you should be fine. It is included on the cd under /arch/begnners-guide.txt (or something like that).

---

### Post by diwas on 2009-01-31
> **smartboyathome said:**
> Just follow the [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") and you should be fine. It is included on the cd under /arch/begnners-guide.txt (or something like that).
Thank you! :)

---

### Post by dannytatom on 2009-01-31
> **smartboyathome said:**
> Just follow the [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") and you should be fine. It is included on the cd under /arch/begnners-guide.txt (or something like that).

I just installed Arch on my laptop last night following the Beginner's Guide and it was a pretty smoothe installation.  Only real problem I had was downloading the wrong video driver, had to get the Intel ones for my resolution to go above 1024x768.  Didn't take but a second, though.

I still have a couple bugs like not being able to set my time right, but all in all I'm in love with it. :D

---

### Post by kerry_s on 2009-01-31
> **dannytatom said:**
> I just installed Arch on my laptop last night following the Beginner's Guide and it was a pretty smoothe installation.  Only real problem I had was downloading the wrong video driver, had to get the Intel ones for my resolution to go above 1024x768.  Didn't take but a second, though.

I still have a couple bugs like not being able to set my time right, but all in all I'm in love with it. :D

check your bios, make sure the time is right in there.
you can also try> pacman -S openntpd
add> @openntpd
to your daemons in /etc/rc.conf

---

### Post by handy on 2009-01-31
> **dannytatom said:**
> 
I still have a couple bugs like not being able to set my time right, but all in all I'm in love with it. :D

Welcome to Arch. :-)

I have found after 9 months of using Arch that my appreciation & enjoyment of it just keeps on growing, which is nice.

As far as your time problem is concerned, have another look at the following, as your problem very likely stems from your locale settings:

*_[http://wiki.archlinux.org/index.php/Locale](http://wiki.archlinux.org/index.php/Locale)_*

*_[http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Flocale.gen](http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Flocale.gen)_*

---

### Post by dannytatom on 2009-02-01
Thanks kerry_s and handy.  My locale is set right, but running 'date -s date/time' seems to have worked.  Still works after reboot at least, not sure if its the _best_ way of setting it.

@handy:  I have #! on my desktop, Arch on my laptop.  The laptop is horrible in comparison, but I haven't touched the desktop since installing Arch. :P  Need to put arch on the desktop, just need to look into installing it with a seperate home partition.

Anywho, thanks to the both of ya. :D

---

### Post by mips on 2009-02-01
> **dannytatom said:**
>  Need to put arch on the desktop, just need to look into installing it with a seperate home partition.

Thats easy as it is part of partitioning and setting mount points. Just create a partition for /home. Next set the mount point for that partition as /home. Arch does the rest.

[http://wiki.archlinux.org/index.php/Beginners_Guide#Partition_Hard_Drives](http://wiki.archlinux.org/index.php/Beginners_Guide#Partition_Hard_Drives)
[http://wiki.archlinux.org/index.php/Beginners_Guide#Set_Filesystem_Mountpoints](http://wiki.archlinux.org/index.php/Beginners_Guide#Set_Filesystem_Mountpoints)

---

### Post by dannytatom on 2009-02-01
Well I already have a seperate home partition, I'll give it a go real fast.  Really just scared to **** it up as I have tons of important stuff on the home partition. :P

Thanks for the links. :D

---

### Post by handy on 2009-02-01
> **dannytatom said:**
> Well I already have a seperate home partition, I'll give it a go real fast.  Really just scared to **** it up as I have tons of important stuff on the home partition. :P

Thanks for the links. :D

I don't want to sound like a nag, but if it is important,you really should have it backed up anyway. :-)

---

### Post by dannytatom on 2009-02-01
> **handy said:**
> I don't want to sound like a nag, but if it is important,you really should have it backed up anyway. :-)

Ha, doesn't sound like nagging to me, was a good suggestion. :P  I should back up, only way to do that is to get the two computers networked, something I have yet to do with any linux distro (never had a need).  I was putting it off as i'm a bit lazy when it comes to things like that, but it's probably in my best interest to man up and do it. :P

---

### Post by handy on 2009-02-01
> **dannytatom said:**
> Ha, doesn't sound like nagging to me, was a good suggestion. :P  I should back up, only way to do that is to get the two computers networked, something I have yet to do with any linux distro (never had a need).  I was putting it off as i'm a bit lazy when it comes to things like that, but it's probably in my best interest to man up and do it. :P

The following link is probably all you will need with any luck:

*_[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS+file+sharing](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS+file+sharing)_*

**[Edit:]**  Here is the Arch page, which I probably should have posted instead of the one above ;-):

*_[http://wiki.archlinux.org/index.php/Nfs](http://wiki.archlinux.org/index.php/Nfs)_*

---

