---
title: "64Mb RAM vs. Ubuntu"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by drahmad on 2007-01-23
Hi and apologies if this has been answered elsewhere.

Someone suggested Ubuntu for my old secondary laptop which is a Thinkpad 390x with Celeron 400, 6.4Gb HDD, and only 64Mb RAM.

I've looked but haven't succeeded as yet to get a compatible RAM upgrade.

I'm currently just fooling around - I would really like to try to install Ubuntu and see what it's all about - but when it says "requires 192Mb RAM for install, is that an absolute? ie. does it actually stop you installing if you have less? Or will it just run slow?

I can cope with it running slow at the moment, but would prefer not to download 700Mb that I can't use if I can help it.

Thanks in advance.

---

### Post by Atomic Dog on 2007-01-23
I have never tried to install it on only 64 meg.  I'm guessin it would boot but the drive would be thrashing a lot.

Try DSL linux instead?  It's pretty thin.

---

### Post by meng on 2007-01-23
Forget about Ubuntu (with GNOME). Perhaps Fluxbuntu instead?

---

### Post by drahmad on 2007-01-23
Thanks everyone, please keep the suggestions flowing in. Do you need to know anything more about the specs?

I was hoping to get another 256Mb of RAM and run ubuntu as suggested, but given that this is going to be a *third* computer that I'm just going to be fiddling around with, it wouldn't be a disaster to install something now, and then completely reinstall ubuntu later if I got my hands on more RAM.

Actually - I can actually get 192Mb going so would ubuntu be ok with 192 or not?

---

### Post by meng on 2007-01-23
With 192 MB, I would suggest the following:
get Xubuntu rather than Ubuntu, **and**
install from the Alternate CD rather than the Live CD

---

### Post by drahmad on 2007-01-23
What are the differences with the alternative CD? I wasn't able to find those differences for myself.


Edit: I just saw on the Xubuntu site that I "can" run it on 64Mb of RAM though 128 is recommended. I think I might take the plunge and see for myself (if it's slow, then so be it at least initially). DSL just looked a little less friendly for me :/

---

### Post by MiloLinux1221 on 2007-01-23
If it said at least 192mb of ram needed and you have that all should work out okay. My advice would be to dont even bother throwing it on the 2nd or 3rd party computer put it right on your primary I just did, I doubt I'll ever go back to windows again (aside from running it in linux for macromedia/games) 
 Just my two cents

---

### Post by Henry Rayker on 2007-01-23
The differences, as far as I know, between the two disks is the Alternate doesn't have the live cd functionality (and has more detailed setup) but it walks you through the setup and all, so it should be just fine...

---

### Post by kuja on 2007-01-23
The Live CD requires a minimum of 192MB of RAM. The Alternate CD requires just over 128MB ... I tried an install with the alternate CD with 128MB and it was swapping out, but I let it sit for a while with no apparant progress and it managed to finish, it just took a while. I guess you can install with 64MB of RAM, it would just take a while, and you'd better have plenty of swap space ready. with 64MB of RAM, avoid any of the "big" desktops like KDE or GNOME, go with something light like Fluxbox or IceWM

---

### Post by meng on 2007-01-23
> **drahmad said:**
> What are the differences with the alternative CD? I wasn't able to find those differences for myself.
The major difference is that the Alternative CD just runs a text-based installer, whereas the Live CD runs a live desktop from which you have the option of installing, at the same time as running a live desktop, which is obviously more demanding on resources. There are some minor differences.

---

### Post by drahmad on 2007-01-23
I'm downloading xubuntu and will see how it goes. Thanks again for the suggestions and I'll investigate them further when I get a chance. Linux is all completely new to me so the suggestions don't make a lot of sense to me right now but I'm sure I will be able to search those terms being referred to.

---

### Post by veli on 2007-01-23
see this thread:

[http://ubuntuforums.org/showthread.php?t=62650](http://ubuntuforums.org/showthread.php?t=62650)

and my guide for lightweight Gnome. 

[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

You also can install only XFCE 4 without all programs in xubuntu.

Or if you follow the guide, instead of gnome you just do:

sudo apt-get update
sudo apt-get install xfce4 thunar

and you'll get all packages for the desktop with no programs.

Here are two screenshots (after fresh reboot) of running Gnome lite, and XFCE 4.4. Xfce consumes a bit less memory than Gnome, but I can't find any significant boost in performance. My comp is old PIII-660 MHz, 256 RAM. You could save some memory by not using weather, mixer and other applets. But my RAM is 256 MB, with 64 MB the situation might be different.

---

### Post by drahmad on 2007-01-23
Thanks for that. 

I must admit that I went a little cross-eyed reading some of it (because I'm a n00b). I don't even really understand the difference between GNOME and any alternative.

I think I've worked out now that GNOME is one way of managing the desktop, and that Xubuntu doesn't use GNOME.

I think as a n00b GNOME probably looks like what I would like, but I will give Xubuntu a try once I finish the download and go from there.

As I've said, this is my 3rd computer so it's not important if there is "down time" or it doesn't work properly. I want to learn more about Linux on that system, and that's the main intention. I'll continue trying to source some RAM as ubuntu does seem rather nice.

---

### Post by deadgobby on 2007-01-23
Gnome and KDE have a higher ram requirement than Xwindows or known as XFCE. Total different type of desktop. Even if your boost your ram. If your are running a 386 or 486 cpu. Gnome may be crawling. Even with older 586 like a PII. X Windows or XFCE will be the best for that system. There is other distro that can run on light stuff. Like Damn Small distro
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
DSL have lots of updates and they seems to keep their eye on the ball.

Gobby

---

### Post by zgornel on 2007-01-23
For 64 mb ram computers fluxbox is ideal. It's a bit spartan but it does the job. Gnome/KDE should be used on PIII or higher cpu's with at least 256MB of ram.

---

### Post by drahmad on 2007-01-23
I guess I'm spoilt when I'm used to running OS X on my primary computer :)

DSL - I was a little put off the by "primitive" screenshots. I know I shouldn't judge by cover, but it didn't look as "friendly" for a total Linux n00b. And once again I know looks can be deceiving...

Thing is that I can afford to keep installing new distros to see what I like. It's hobby time for me and there won't be anything on the computer that I'll have to backup in case I lose, etc.

---

### Post by noalternative on 2007-01-23
Try [ubuntu-lite]("http://www.ubuntulite.org"), it is a complete icewm distro with aps like abiword, gaim and gnumeric.  It should work much better, on a machine with that little ram, than gnome based ubuntu , kubuntu or even xubuntu. Ubuntu and Kubuntu shouldn't even be tried with huge memory upgrades on your machine because they are processor intensive.  Here are some instructions for installing ubuntu-lite-desktop from repositories.
[INDENT]**Install UbuntuLite through repositories**

     At this point I want to thank **[Blackpaw]("http://ubuntuforums.org/member.php?u=31207")** for providing us repositories. 
   1. First you have to install Ubuntu on your computer. Boot from the normal Ubuntu CD and at the boot: prompt, enter server.    
 boot: server   The rest of the install will be similar to a normal install. When it is done, you will have a very basic system: networking, apt, and a shell. 
   2. When the install is done, reboot and log in and edit your sources.list:  
 $ sudo nano /etc/apt/sources.list   3. Enable universe by removing the ‘#’ from :  
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe   4. Then add the following line at the end of sources.list:  
 deb [http://blueeyedcreature.net/ubuntu](http://blueeyedcreature.net/ubuntu) ./    Save and close 
   5. Refresh apt’s package list (index) and start the ubuntu-lite-desktop install:  
 $ sudo apt-get update
$ sudo apt-get install ubuntu-lite-desktop  And after you are done, restart your machine and you will find yourself in the WDM login manager. It’s an extension of XDM, the regular X11 login manager. 
  Login as user and you have a working Ubuntu Lite system with IceWM as window manager installed. You will also have many other useful applications installed. 
   Check the whole list on the [Package List Page]("http://www.ubuntulite.org/dokuwiki/doku.php?id=applications")

[/INDENT] Hope this helped!:wink:

---

### Post by ragadanga63 on 2007-01-27
The best OS for a system like that will be Linux Puppy.  It's fast, and can be customized to your needs.  I've tried it and fell in love with it.  You can read about Puppy from this link:  [www.puppylinux.org](www.puppylinux.org).  Believe me, it's easier than Ubuntu.

---

### Post by PurplePenguin on 2007-02-08
And Puppy, for me, seems to be head and shoulders above Damn Small Linux in terms of being easy to use and set up.

---

### Post by uncreative on 2007-02-08
I have that exact same laptop only with 128mb of ram and it runs Ubuntu Dapper just fine.

In fact its pretty darn quick.

---

### Post by Bartender on 2007-02-08
Finding memory for that unit seems like a relatively easy task -

[http://www.memoryx.net/ibmth3926me.html](http://www.memoryx.net/ibmth3926me.html)

[http://www.computerlaptopmemory.com/ibm_laptop_memory.html](http://www.computerlaptopmemory.com/ibm_laptop_memory.html)

[http://www.edgetechcorp.com/memory/upgrade.asp?cid=18101](http://www.edgetechcorp.com/memory/upgrade.asp?cid=18101)

It might be hard to justify spending $100 or more for an old lappy...

---

