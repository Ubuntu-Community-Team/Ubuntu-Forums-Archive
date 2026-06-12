---
title: "Crippled Heron"
date: 2008-09-23
forum: Apple Hardware Users
---

### Post by explorer59 on 2008-09-23
I am attempting to install U8.04 onto my PM G4 MDD Dual 1GHz. Available display options are DVI, or VGA using a DVI-VGA adapter. I do not have an ADC display at hand, but could get one if necessary. 

If I boot from the v.8 install CD, I am left with a black screen; using 'live video=ofonly' makes no difference with either display option. As a workaround, I tried installing v.6, then upgrading (I figured I might have better results starting from the last 'officially supported' version). I was able to use either DVI or VGA, however, v.6 did not give me the full range of resolutions that I should have received from my video brd (ATI Radeon 9000 Pro RV250). Also, something got botched during the u/g, leaving me with no fonts, just little rectangles. 

Next, I went through the same process, but this time starting with a v.7.10 install CD. Booting while using the DVI connection results in a black screen, same as v.8, and again, 'live video=ofonly' has no effect. Video is OK using VGA. After installing the usual batch of initial updates, I was given the option to upgrade to v8.04, which I did. I installed the u/g and rebooted. Everything appeared normal up to the login screen. A few moments after the login screen appears, the speed drops to a crawl.

I am quite certain that it is not due to some particular glitch during this install; I ended up with exactly the same problem a few days ago using essentially the same sequence, except I was using Kubuntu.

---

### Post by mkvnmtr on 2008-09-23
When you restart and it begins to load press tab. You should see a page of options with a prompt at the bottom of the page. This is where you will see anything you type. I believe I used Linux video=ofonly no splash. Type that and press enter. If it does not work to get you to the desktop restart and do the same thing pressing tab but try another option. I think the first one will work but try them one by one till one works. You need to type it in exactly as you see it with capitals and spaces when they are there.

---

### Post by explorer59 on 2008-09-24
In my initial post, I should have mentioned that I *can* log in, but the system responds *very* slowly - this Heron is wading in honey.

From your message, I'm not clear on when I'm supposed to press the Tab key. When I restart the computer, the first screen that comes up is:
   First stage Ubuntu bootstrap
   Press l for GNU/Linux,
           x for OSX,
           c for CDROM

The next screen is:
   Welcome to yaboot version 1.3.13
   Enter "help" to get some basic usage information
   boot:

If I press tab at this point, I just get a line saying:
       Linux               old
   boot:

If I type 'help', I indeed get *BASIC* help info, no list of options as you mention. If I type your suggested line at the "boot:" prompt, the computer eventually boots up but is still very slow.

---

### Post by mkvnmtr on 2008-09-24
I pressed tab when the first page came up. If I waited I would have no luck. It seems you had an earlier distro installed. So did I. I could never get an upgrade to work. I found the advice to press tab in the forums but they did not say when or give any idea of how to do it. As someone new to all this I had no idea. I tried about 50 ways before I hit the one that worked. For this reason I try to explain things that seem simple but for a newcomer they might not see when to do something at the right. It doesn't matter if it is a slow boot. Once you get installed it should be normal.

---

### Post by explorer59 on 2008-09-24
Still no luck with the Tab key. As I described, I had to start with the earlier distro because the v.8 CD boots to a black screen regardless of what video option I try.

Also, I *do* get to the login screen and eventually the desktop, but everything about the system runs very very slow - mouse movement, keyboard - everything.

---

### Post by explorer59 on 2008-09-24
On a hunch...
Pressing the Tab key to get the options list only works when booting the distro CD. That said, the proper line to type is:
live-nosplash video=ofonly

Booting from the v.8 CD and using the above option eventually presents me with what looks like some sort of debug dump, but still no live desktop.

---

### Post by mkvnmtr on 2008-09-24
I don't think with my limited experience I can help you get any more. You know that the disk will be much slower that the install.  The disk just turns slower than your hard drive. If it is very slow We might ask how much ram you have. Your processor is fast enough but I did not see where you said how much ram you have. I am sure someone els will be able to get you further along, Some of these guys really know what they are doing.

---

### Post by Bikerbob on 2008-09-24
I have 804 running on a G4 dual800. I installed fresh using the live CD.. no issues.
Now the video card is NOT Radeon. It is Rage128 agp 16mb I think.. since I really dont use linux for gaming the video is not important to me.

But I will tell you this, I tried to install on a G3 with Radeon, this computer with a Radeon 7000 and had issues. If you can post your xorg.conf and your Xorg.0.log it will help people figure it out. 

Check the wiki pages as well. There are a number of great doc pages on getting ATI cards working.

Can you get the live 804 to run? Is this just an issue AFTER an install? or can you not get the live CD to run from the CDrom no install?

James

---

### Post by explorer59 on 2008-09-25
Summary from above thread:
- Ubuntu and Kubuntu ver.8 live CDs boot to black screen. Booting using the '-nosplash' option eventually results in debug dump (I can provide a photo if it would be helpful
- ver. 7 live CDs and installed Systems work only with DVI-to-VGA adapter
- Upgrading an installed ver.7.10 to 8.04 results in the ultra-slow response problem; the reason for this thread. 
-ver. 6 live CDs and installed Systems will work with DVI or VGA, but only up to 1024x768

The ultra-poor performance is my main concern. Getting the DVI output to work is a secondary issue.

I would be happy to post the Xorg... files; where would I find them.

---

### Post by roost3r on 2008-09-27
I know this likely does not help much, but after reading your posting, I decided to try 8.04 on my PowerBook 1.67GHz. This time it actually booted into the live CD (I used the video=ofonly option). From there I installed it onto the remaing free space that I had previously set aside for this purpose. Initially I oculd not get the wifi to work until I read on these forums that someone simply removed the module (modprobe -r bcm43xx) and then reinstalled it (modprobe bcm43xx). I did the same and my wifi was up and running. So far all is well, but I have not rebooted since re-install the module. I hope it sticks!

---

### Post by tiresia on 2008-09-27
> **explorer59 said:**
> 
I would be happy to post the Xorg... files; where would I find them.

/etc/xorg.conf

Anyway to install Ubuntu on those machines is to use the Alternate CD. So I would have a last try with Ubuntu Hardy (8.04) from an Alternate CD. Just start pressing C

If you have any PCI extra Card remove it, before installing.

---

### Post by cyberdork33 on 2008-09-27
> **tiresia said:**
> /etc/xorg.conf
That's /etc/X11/xorg.conf

---

### Post by explorer59 on 2008-09-27
> **cyberdork33 said:**
> That's /etc/X11/xorg.conf

Here's the xorg.conf file, but I don't think it has any bearing on my primary problem, which is the performance problem. 

I'll try a nuke-and-pave and install from the alternate CD.

---

### Post by explorer59 on 2008-09-28
> **explorer59 said:**
> I'll try a nuke-and-pave and install from the alternate CD.

Boot Alternate CD using DVI:
- Installer stalled with message that it couldn't locate the CD (same as macpeirox - [http://ubuntuforums.org/showthread.php?t=929830](http://ubuntuforums.org/showthread.php?t=929830) except in English ;-). 

My solution was to burn a 2nd Alternate CD, boot from an external CD drive with duplicate CD in internal drive. This time the installer went as far as 'Starting up the partitioner', but stalled at 55%,

Restarted using DVI-VGA adapter; the installer completed the process, but upon booting the installed System, I still experienced the original bad performance issue.

Back to square one. 
Re-read the thread... noticed note: > **tiresia said:**
> If you have any PCI extra Card remove it, before installing. ...removed long-forgotten PCI-FW card...

Tried the v.8 Live CD using DVI using 'live video=ofonly' option, and it booted successfully. The installer also ran successfully, but again, booting the installed System leaves me with a near-frozen Heron.

Back to the Alternate CDs
- Tried again using DVI, but Partitioner still stalls at 55%. 
- Repeat using VGA, but installed System is still unusable

Time to nuke this Heron...
Back to Gutsy

---

### Post by tiresia on 2008-09-28
> **explorer59 said:**
> 
Tried the v.8 Live CD using DVI using 'live video=ofonly' option, and it booted successfully. The installer also ran successfully, but again, booting the installed System leaves me with a near-frozen Heron.

Back to the Alternate CDs
- Tried again using DVI, but Partitioner still stalls at 55%. 
- Repeat using VGA, but installed System is still unusable



What do you mean with 'near-frozen' and with 'unusable'?

---

### Post by explorer59 on 2008-09-28
> **tiresia said:**
> What do you mean with 'near-frozen' and with 'unusable'?

The System boots normally, but as soon as the login screen appears, keyboard input, mouse movement and all other response lags by several seconds to many minutes. 

That's what this thread is all about...

---

### Post by tiresia on 2008-09-28
I don't have any experience with g4, but it looks like a problem with the Grafic Card.
Do you have a similar issue like here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/93509](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/93509)

In the last post is suggested to try with Ubuntu Intrepid:
[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

I would have a try also with Debian Lenny
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by explorer59 on 2008-09-28
> **tiresia said:**
> I don't have any experience with g4, but it looks like a problem with the Grafic Card...

Those reports might be useful for getting my DVI video issue fixed, which is present with ver.7, but NOT with ver.6

MY PRIMARY ISSUE IS WITH THE LAGGY RESPONSE/IMPOSSIBLY POOR PERFORMANCE

---

### Post by pxwpxw on 2008-09-28
**explorer59**

If you can get to terminal or a console using Contol-Alt-F1 (or f2 ...f6.)
then run
```
  
top

```
and watch it for a while, it might show what/where is the problem.

---

### Post by ubuntubrian on 2008-09-28
I have no idea of the relevance but I had a really poor performing install of Hardy on my TiBook G4 and found that after I uninstalled xgl-xserver the performance was as good as in Dapper, my previous version. No desktop effects but the performance is worth it as I can watch videos, etc.
I have Intrepid installed on my old lombard and along with all of the alpha issues (have to run KDE as Gnome doesn't work) I the jerky video performance but there is no xgl-xserver. Video is now all compiz and xorg soI'm not sure what to do...

---

