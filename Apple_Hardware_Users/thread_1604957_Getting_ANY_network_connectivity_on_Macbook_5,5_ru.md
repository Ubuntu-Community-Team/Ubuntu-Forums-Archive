---
title: "Getting ANY network connectivity on Macbook 5,5 running 10.10"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by larrinski on 2010-10-24
Anyone have success setting up either wireless or ethernet connectivity on a Macbook Pro 5,5 on the 10.10 Maverick install?
 
Normally in the past with 10.04, etc... I just plug in my ethernet cable and update my wireless using "sudo apt-get install bcmwl-kernel-source", but I can't even get my ethernet to work...
I tried to load it from the live CD once logged in but couldn't figure it out...
Any advice would be greatly appreciated. :)

I am trying to switch over permanently to Ubuntu on my Macbook Pro, but need wireless to work...

---

### Post by dalucky1 on 2010-10-25
Do you have any network connectivity when you boot from the live CD? It's weird but I was able to get connectivity via the live CD but not post install. 

Anyway, I was lucky enough to have the wired connectivity post install. Took me a little while to get the wifi up and running...

Download this tarball; [Wireless driver tar]("http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86-32_v5.60.246.2.tar.gz")

If you're somewhat familiar with the CLI then just untar it and see the README.txt for compilation instructions. 

If you're super new...then let me know and I'd be more than happy to explain the process to you. 

-cheers.

---

### Post by larrinski on 2010-10-25
Thanks! I will mess around with it. I'm OK in the command line. At least it doesn't scare me anymore. haha. 
I will post if I get stumped. 
Cheers!

---

### Post by larrinski on 2010-10-26
Well, I followed the instructions pretty well I think(didn't get any errors), but obviously screwed up as I still have no connections. I even followed the READme.txt twice...rebooted etc...

I did try to see if I could get online from the Live CD but it didn't work as well. When I select the icon, I see eth0 but it won't connect. 

Another thing I also notice isn't quite right on my install is when I go to system-->Admin--> I don't see "hardware drivers", but see "additional drivers". When I was doing my install I didn't select proprietary drivers as I figured it would need to have wireless access. Would that have messed something up?

---

### Post by dalucky1 on 2010-10-26
This is strange...btw are you using Ubuntu 10.10? I have the same exact Mac (5,5) and for some strange reason I had wireless on the live CD but not post install. 

You might wanna select proprietary drivers btw as the broadcom driver might indeed be in there. If you followed all the instruction then it then the wifi icon should of popped up on the top right taskbar. 

Wish I could of been of more help but I'm a complete n00b when it comes to Linux. I gave up on ubuntu seeing as how for the life of me I couldn't figure out the sound drivers. I got ubuntu to learn the *nix terminal but I figured the OSX terminal will suffice. 

Have you gotten the sound to work on your rig?

---

### Post by larrinski on 2010-10-27
No, I haven't even gone there yet. I usually work on the wireless first. Most of the time I need quiet after the kids go to bed, and realize I haven't heard a thing in hours! lol. 

Thanks for trying, and if I get it up and running, I will post my results.
Cheers,

---

### Post by linuxopjemac on 2010-10-27
look also at this thread:
[http://ubuntuforums.org/showthread.php?t=1604984](http://ubuntuforums.org/showthread.php?t=1604984)

I gave him a solution to have a wired connection, it will also work for your MacBook.

---

### Post by larrinski on 2010-10-27
> **linuxopjemac said:**
> look also at this thread:
[http://ubuntuforums.org/showthread.php?t=1604984](http://ubuntuforums.org/showthread.php?t=1604984)

I gave him a solution to have a wired connection, it will also work for your MacBook.

Thanks for the post. I ran the commands and edited my interfaces file. When I ran sudo ifdown eth0, I got the same response of interface eth0 not configured. Running ifup eth0, I got the same "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4", but it kept looking, and looking, and eventually timed out...

So, no luck so far...It was going well up until it timed out...

---

### Post by Jales on 2010-10-27
I have a MBP 55 too, and the ethernet just works out of fresh install. But not with my wireless. Had to follow the instruction in this page ( [https://help.ubuntu.com/community/MacBookPro5-5/Maverick](https://help.ubuntu.com/community/MacBookPro5-5/Maverick) ) to get it work.

---

### Post by larrinski on 2010-10-27
> **Jales said:**
> I have a MBP 55 too, and the ethernet just works out of fresh install. But not with my wireless. Had to follow the instruction in this page ( [https://help.ubuntu.com/community/MacBookPro5-5/Maverick](https://help.ubuntu.com/community/MacBookPro5-5/Maverick) ) to get it work.

Wow. That is good news though. The 5,5 page isn't very in-depth. lol. 
I will probably just do a fresh install and see if that gets me Ethernet access to start...

---

### Post by larrinski on 2010-11-05
I have been playing a bit with  Mint 9 & 10 installs to see if that would get me an ethernet connection. No luck. No one seems to have any answers and the various methods I've tried are getting me nowhere. 

Is there anyone that can help me out? This has been the worst Ubuntu install for me(for connectivity), and my Macbook Pro is not even bleeding edge...It surprises me that running 10.04 on a USB full tim on my IBM Thinkpad worked out of the box, but a full install of either Mint 9/10RC or Ubuntu 10.04/10.10 on my Macbook Pro has no connectivity or sound...Even a full install on an Acer Aspire ran pretty much out of the box...Is an Apple that hard to configure?

---

