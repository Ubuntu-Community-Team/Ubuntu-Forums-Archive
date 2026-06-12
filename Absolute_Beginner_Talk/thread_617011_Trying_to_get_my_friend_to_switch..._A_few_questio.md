---
title: "Trying to get my friend to switch... A few questions."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by cmlewin on 2007-11-18
1. He works at home sometimes and needs the MS Office programs (Excel, Powerpoint, etc)

2. He really likes the compiz effects and I just want to make sure they'll run on his system.

Specs:
HP Pavilion Desktop
Pentium D CPU 2.66 GHz
2.67 GHz, 1.93 GB of RAM
ATI Radeon Xpress 200 Series

3. I think the best thing would be to dual boot, but I'm not sure of the exact steps to make the partition work properly without erasing anything and he has a lot of stuff on here that I wouldn't want to lose.

Thanks and I'm sure I'll have more questions so be prepared :-)

---

### Post by finer recliner on 2007-11-18
ubuntu comes with openoffice, which has pretty good support for reading and editing .doc, .xls, and .ppt files.

---

### Post by geirha on 2007-11-18
2. One way to find out is to boot the liveCD and enable extras under System -> Preferences -> Appearance -> Visual Effects

3. The ubuntu installer will give the option to reduse the size of the windows partition, and install ubuntu on the freed up space. Defragment it in windows first though.

---

### Post by irish_flu on 2007-11-19
If you decide to dual-boot, make sure the Windows drive is freshly defragmented (like, just before you power it down) and BACKED UP.

Anytime you're messing around with an existing disk partition, bad things can happen. The Live CD does a great job, but once in awhile stuff goes poorly (especially if some unknown thing is wrong with the NTFS partition before you start).

---

### Post by jaybombalous on 2007-11-19
its your friends pc, best thing to do is buy an cheap source of HD space to install it on and do it that way. Then u won't have to explain how u managed to erase everything even though it should have worked right out of the box.

---

### Post by cmlewin on 2007-11-19
> **geirha said:**
> 2. One way to find out is to boot the liveCD and enable extras under System -> Preferences -> Appearance -> Visual Effects

3. The ubuntu installer will give the option to reduse the size of the windows partition, and install ubuntu on the freed up space. Defragment it in windows first though.


On the live CD the effects won't enable, but don't i need to install the restricted ATI drivers that support the 200 series...

Also when I click 'guided' use free space it says there's not enough free space

Then when I try to pick the NTFS partition to space out how much I want to do manually it says "No root file system is defined" and asks me to fix it in the partition menu.

If I have an extra internal HD, would it be easier to just plug that in, format it, and install Ubuntu on just that? Then how does booting work b/c I would need to chose a master drive each time right... or something like that?

HELP! Thanks again.

---

### Post by geirha on 2007-11-19
> **cmlewin said:**
> On the live CD the effects won't enable, but don't i need to install the restricted ATI drivers that support the 200 series... That's probably true. It's way better than my ati card according to the specs I found with google, so as long as the restricted driver works, compiz fusion should work fine.

> **cmlewin said:**
> Also when I click 'guided' use free space it says there's not enough free space

Then when I try to pick the NTFS partition to space out how much I want to do manually it says "No root file system is defined" and asks me to fix it in the partition menu.
 Hm, isn't there an option saying it will resize the windows partition to make space for ubuntu?

Anyway, you can abort the install at that point, choose System -> Administration -> Gnome partition editor and resize the windows partition yourself. Then tell the installer to use all available free space afterwards.

> **cmlewin said:**
> If I have an extra internal HD, would it be easier to just plug that in, format it, and install Ubuntu on just that? Then how does booting work b/c I would need to chose a master drive each time right... or something like that?

HELP! Thanks again.
That will work. In the BIOS you can usually set the boot order so that USB-storage devices boots before the CD and harddrive(s). Then, if you remove the external harddrive, it should boot the harddrive with windows instead. I tried this with an usb memorystick :)

Don't format it though, just remove some partitions on it so there are some free space, and tell the installer to use the free space. The installer will format it anyway. (no need to do it twice!)

---

### Post by cmlewin on 2007-11-19
> **geirha said:**
> That's probably true. It's way better than my ati card according to the specs I found with google, so as long as the restricted driver works, compiz fusion should work fine.

 Hm, isn't there an option saying it will resize the windows partition to make space for ubuntu?

Anyway, you can abort the install at that point, choose System -> Administration -> Gnome partition editor and resize the windows partition yourself. Then tell the installer to use all available free space afterwards.


That will work. In the BIOS you can usually set the boot order so that USB-storage devices boots before the CD and harddrive(s). Then, if you remove the external harddrive, it should boot the harddrive with windows instead. I tried this with an usb memorystick :)

Don't format it though, just remove some partitions on it so there are some free space, and tell the installer to use the free space. The installer will format it anyway. (no need to do it twice!)

Thanks for all the help.  I didn't want to screw anything up, especially b/c he's unsure as to whether or not he'll keep Ubuntu at all, so I just went with Wubi. 

New and hopefully quick issue however is that the internet connection is now not working and Wubi is on Feisty Fawn still so I wanted to update (and go on the internet of course haha).  I'm on a wired network (Comcast) and using a Motorola SURFboard modem (I think).  Should just be plug and go... Maybe I need to reset the router for the IP address or something. Ayudame please once again.

Thanks and thanks and thanks! :)

---

### Post by geirha on 2007-11-19
An educated guess would be that you have internet, but lack the ip-addresses of the dns-servers. Try ```
ping 91.189.94.186
ping ubuntuforums.org
```

Do both fail?

---

### Post by cmlewin on 2007-11-19
geirha - thats pretty accurate (haven't tried the ping's but i'm sure they'll fail as no website loads no updates possible as no servers can be reached) but it does say i am connected.

how do i get those gold coated ip-addresses i so seek? (sorry, its 3am here in D.C.)

---

### Post by geirha on 2007-11-19
They really should've been provided by the router along with the ip-address, but you can always dig them out of windows. I think "ipconfig /all" in windows' commandpromt will display them. Or you can simply use the opendns servers [http://www.opendns.com/](http://www.opendns.com/) (bottom right corner)

---

### Post by cmlewin on 2007-11-19
> **geirha said:**
> They really should've been provided by the router along with the ip-address, but you can always dig them out of windows. I think "ipconfig /all" in windows' commandpromt will display them. Or you can simply use the opendns servers [http://www.opendns.com/](http://www.opendns.com/) (bottom right corner)

Are the openDNS servers really slow?

Also why do I have to do all this as on my laptop I just plugged it in and went...

---

### Post by geirha on 2007-11-20
It sounds to me like it should've gotten the dns servers right the first time (since it obviously works "out of the box" with windows, right?) 

If you open /var/log/daemon.log and look for "DHCP" and "NetworkManager", there might be some error messages there that might give you a clue of what's going wrong.

Wubi looks cool btw, wish I had windows so I could try it out :)

---

### Post by stchman on 2007-11-20
> **cmlewin said:**
> 1. He works at home sometimes and needs the MS Office programs (Excel, Powerpoint, etc)

2. He really likes the compiz effects and I just want to make sure they'll run on his system.

Specs:
HP Pavilion Desktop
Pentium D CPU 2.66 GHz
2.67 GHz, 1.93 GB of RAM
ATI Radeon Xpress 200 Series

3. I think the best thing would be to dual boot, but I'm not sure of the exact steps to make the partition work properly without erasing anything and he has a lot of stuff on here that I wouldn't want to lose.

Thanks and I'm sure I'll have more questions so be prepared :-)

His PC will work with Ubuntu.  I have a laptop with an ATI Xpress 200M and I enabled the restricted driver.  I currently have desktop effects disabled since the driver has compatibility issues with Compiz.

Does your friend use broadband or dialup?  If they use dialup Winmodems are poorly supported under Linux.  Broadband is teh only way to go.

If he does average duties with MS Office then OO will be a good fit.

Just use the live CD and create some free space (40GB) or so using gparted.  Once done tell the installer to use the largest continuous free space.  Use my software install script for whichever version you install:

[http://www.stchman.com/install_scripts.html](http://www.stchman.com/install_scripts.html)

Just remember to enable all the repositories.

Hope this helps.

---

