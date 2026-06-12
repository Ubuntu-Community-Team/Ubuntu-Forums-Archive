---
title: "Mouse lags a lot in bottom right corner."
date: 2011-06-20
forum: Any Other OS
---

### Post by Tsportmat on 2011-06-20
Hello everyone. I was a windows user until I installed Ubuntu on my old laptop. I liked it a lot; however, upon upgrading to Natty I didn't like Unity at all (or maybe I just REALLY liked GNOME 2.x). 

Anyway, I decided to switch to Linux Mint, and make it look pretty much how Ubuntu Classic looked - which was fine. I then installed it onto my desktop, and performed the necessary tweaks to get it running how I wanted - which was fine.

I have now noticed, however, that my mouse seriously lags in the sqaure inch at the bottom right of my screen (23" if you want that in perspective), it will take a couple of seconds to free it up. 

Now I've deleted the bottom GNOME bar, with no success. In fact, the problem still occurs on the login screen. I've played about with mouse drivers with no  success either.

Could anyone offer any advice please? I'm quite a beginner to all of this, so I don't know what else to do!

Thanks in advance.

---

### Post by fabio.hipolito on 2011-06-20
Hi,

same problem here, my mouse also gets "locked" in bottom right corner.

I am running Ubuntu 11.04 AMD64 on a Dell Optiplex 990 and I use Ubuntu Classic as the desktop environment, same problem with the standard Ubuntu(Unity) desktop.

Best regards.

---

### Post by fabio.hipolito on 2011-06-20
Hi again,

after to searching a bit I found this [thread]("http://ubuntuforums.org/showpost.php?p=10953146&postcount=35") in I ubuntu forums and tried it. I worked for me.

So just
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```
and then reinstall the proprietary drivers for ATI using program System/ Administration/ Additional Drivers.

Best regards.

---

### Post by Tsportmat on 2011-06-21
Hi Fabio, thanks for your reply.

I tried the steps which you outlined - unfortunately they didn't work for me; although, I guess that it is an ATI problem. 

I'm running a Sapphire ATI Radeon 5770 Vapor-X.

---

### Post by Tsportmat on 2011-06-21
Hello again. 

After playing about a bit, I did the steps which you said, I also deleted the fglrx folders in /usr/share/lib(32). I then restarted. 

My mouse did not get stuck in the corner! However, upon reinstalling my graphics driver from System/ Administration/ Additional Drivers, and restarting, the problem reoccured!

---

### Post by Perfect Storm on 2011-06-21
Moved to Other OS/Distro Talk.

---

### Post by 4Orbs on 2011-06-21
@Tsportmat-I have the same graphics card as yours. Oddly, the only distro that seems to work for me with the current ati drivers is Xubuntu 11.04 using the "Additional Drivers" installer that comes with the system. I have tried the new drivers on a few other Linux distros (Fedora 15, Salix, Mint 11 and Mint Debian, Debian Squeeze) and had the same mousetrap in the lower right corner. I used the distro-supplied drivers, and when they failed I would purge the fglrx stuff and do a manual install with the driver from the ati website (including version 11.6). Still, the bad spot existed in the lower right corner. However, manually installing an older version of the drivers (10.11 in my case) worked just as well for video and effects as the new drivers and eliminated the bad spot on the desktop.

I'm not saying that this is the best way to fix the problem, but you might find it interesting.

---

### Post by Tsportmat on 2011-06-21
Thanks again for your replies everyone!

I ended up purging once again, went for the reboot, with the intention to install the latest drivers off the ATI site. When I tried to boot it - it didn't boot... I have to go into recovery mode and basic graphic mode. I think tried to install the latest driver. I still couldn't boot into Mint normally so had to go into recovery again. To my surprise, the screen was distorted and the colours seemed inverted/psychedelic... I tweaked and tweaked and couldn't fix this, so I went for the full reinstall.

Upon reinstalling, I installed the ATI driver through the 'additional drivers' menu. The mouse has not got stuck yet!  I can activate my 3D graphics - although I think they're slightly more jerky than before... I've turned them up in CCC - including no tearing, with no problems except a slight degradation in performance. I think this happened before, and when I 'fixed' that, the mouse sticking occurred; I'll leave it how it is for now, and keep you updated.

To cut my life story short :popcorn: - installing CCC from additional drivers on a fresh install appears to work.

---

### Post by 4Orbs on 2011-06-21
Glad you got it working. The jerkiness is probably due to the tear-free setting and will probably affect videos and even cause a slight delay when typing text, passwords, etc.

---

### Post by I[AM]SMRT on 2011-06-30
It's a known issue with Catalyst 11.6: [http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586](http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586)

From what I read, there should be a full fix when 11.7 rolls around (7/15/11 for windows) and the Linux version should follow shortly after.

---

### Post by Tsportmat on 2011-07-01
> **'I[AM]SMRT said:**
> It's a known issue with Catalyst 11.6: [http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586](http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586)

From what I read, there should be a full fix when 11.7 rolls around (7/15/11 for windows) and the Linux version should follow shortly after.

Just what I wanted to hear - thankyou!

---

### Post by ark1-87 on 2011-07-30
I have the same problem still with the 11.7 driver. using an asus ati radeon HD 5770.

---

### Post by sbraz on 2011-08-17
11-7, problem still there.
actually it reappeared somehow, i'm reverting to an old .config of my custom kernel.

ati hd4200

---

### Post by sbraz on 2011-08-17
hello dear future nvidia/intel graphics customers. :)
it is possible that this problem is kernel related, let me explain:

i had the problem with 11-5, i think 11-6 too. 11-7 solved the problem.

since i'm a custom-kernel-addicted i make my own builds.
yesterday i made some changes to my 2.6.39.4 and the problem reappeared! after some tests (purge/install 11-7, undo some latest changes to xorg.conf), i decided to roll back to my latest configutation marked as "ok" and YES there were something wrong with some kernel option.

i'll try tracing this annoyance so we can finally enjoy our lower-right corner. :)

---

### Post by nagylzs on 2012-09-13
> **'I[AM]SMRT said:**
> It's a known issue with Catalyst 11.6: [http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586](http://phoronix.com/forums/showthread.php?56049-AMD-Catalyst-11.6-Linux-Driver-Released&p=214586#post214586)

From what I read, there should be a full fix when 11.7 rolls around (7/15/11 for windows) and the Linux version should follow shortly after.

It was a long time ago, but I still have the same problem! It comes out only when I connect a monitor to my laptop, and use that monitor as the primary (and the only) display. Unfortunately, my laptop has a small display, so I want to use an external monitor.

Why could ATI not fix this problem within a year? It is so annoying!

---

