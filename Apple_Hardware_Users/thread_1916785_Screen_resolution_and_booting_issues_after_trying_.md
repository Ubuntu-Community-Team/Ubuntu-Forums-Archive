---
title: "Screen resolution and booting issues after trying to install on a second HD"
date: 2012-01-28
forum: Apple Hardware Users
---

### Post by canhoto on 2012-01-28
Hi.

I'm currently running Ubuntu (lately Kubuntu) on my main HD. I have Mac OS installed on the other one. I decided to shrink the size of Mac OS and install Ubuntu or another distro on the rest of that drive. I created a new partition and made the Mac OS partition to diminish. Everything went well. Then I tried to install Debian to give it a try. The installer found that HD, the partitioning was ok, but then it failed to install yaboot, so I didn't finish the installation. I picked up a Ubuntu live cd to install it instead of Debian. But the installer didn't find that HD (nor GParted). It only showed my current, Ubuntu running, HD. I tried with other live cd's/installers, and I had the same problem. No other HD found.  Any ideas about what it may be?

But then I had two more problems.

The first (less annoying):
- When I restarted the computer, it booted from Mac OS (on that second HD). I tried to boot it several times and it always starts from Mac OS, unless I choose Linux from the booting screen via the alt key. I can do this all the time, of course, but it's annoying, and I got used to just start the computer and have Kubuntu just in front of me without any concern.

The second (and worst):
- My screen doesn't get filled by my desktop with my usual screen resolution (1440x900). It has a kind of a shift to the left, hiding a good part of the desktop (see picture). To have the full screen I have to choose a lower resolution. Also, it comes back to the default resolution when I reboot, which I appreciate, but not with one third of the desktop hiding!

I tried hard to solve this myself, but I couldn't. So... any help to this three issues:

- HD not found by the installer and partitioner
- Mac OS always wanting to boot first
- Hiding desktop with normal screen resolution?

Thanks

---

### Post by canhoto on 2012-01-30
Well, for the first problem (Ubuntu not finding HD) I found what the problem is: I have this HD attached to an adapter so that Mac OS can recognize there's more than 128 GB of space... because if I attach it directly to the motherboard the rest of the HD (which has 400 GB) will be ignored by poor little Mac OS. But Ubuntu doesn't recognize the adapter. So, has I don' need to use more than 128 GB with Mac OS, I'll attach it to the motherboard and Ubuntu will find it.

I solved the booting problem for now by unplugging the Mac OS HD: it boots from the Main (ubuntu) HD, of course. But I don't know what will happen when I plug it again (to the motherboard).

But I keep the screen resolution problem. I can have it working well at 1280x800. For that I wrote the following line to /etc/kde4/kdm/Xsetup:

> xrandr --output VGA-1 --mode 1280x800

But if I try to use the good resolution (1440x900) it goes back to the "two-thirds" desktop.

I still appreciate any help on this issue.

---

### Post by rsavage on 2012-01-30
From reading other people's posts, if you are going to plug your big hard drive directly into your motherboard then you need to put the ubuntu root partition also within the first 120 or so GBs. Whether this is true or not you will have to confirm.
 
If debian can use the adapter, but ubuntu can't then there must be a missing module. You should track the missing module down and then report it as a bug to ubuntu (against the 'linux' package). Only then will it get fixed for 12.04. I can give you hand with this.
 
Debian yaboot setup may have failed because of the adapter or the pata_macio module (if you tried wheezy). It will still be possible to boot the installed Debian system though (see troubleshooting section of the FAQ).
 
You could try resetting your pram/pmu type thing to fix your screen problem. This should also fix your ubuntu automatic boot problem (or you can just re-run the ybin command).

---

### Post by canhoto on 2012-01-30
> **rsavage said:**
> From reading other people's posts, if you are going to plug your big hard drive directly into your motherboard then you need to put the ubuntu root partition also within the first 120 or so GBs. Whether this is true or not you will have to confirm.
 
If debian can use the adapter, but ubuntu can't then there must be a missing module. You should track the missing module down and then report it as a bug to ubuntu (against the 'linux' package). Only then will it get fixed for 12.04. I can give you hand with this.
 
Debian yaboot setup may have failed because of the adapter or the pata_macio module (if you tried wheezy). It will still be possible to boot the installed Debian system though (see troubleshooting section of the FAQ).
 
You could try resetting your pram/pmu type thing to fix your screen problem. This should also fix your ubuntu automatic boot problem (or you can just re-run the ybin command).

Well...
I plugged the two hd's to the motherboard, since I don't plan to use more than about 60-70 GB with Mac OS. So, the root partition can be within  the 128 GB. I plugged the drives so that the one with my main Ubuntu system is the default, the "master". And it worked. No more booting problems. If I want Mac OS I choose it with the "alt" boot menu, but Ubuntu loads when I start up the computer.

I also managed to install Ubuntu (Lubuntu, more precisely) on the big HD alongside Mac OS. But I can't boot to it! If I press "alt" I just have two alternatives: Mac OS on one drive or my current Ubuntu on the other. So, that's a new problem.

As for the screen problem, I still have it. I reset the pram several times, but nothing changed (which is weird). I also tried to use several xrandr commands. But each time I try the normal screen resolution for this monitor (1440x900), I loose one third of the desktop (like you see in the picture).

I'm running it with 1280x800, but... I loosed the clean and shinny look of my 1440x900 desktop...

---

### Post by rsavage on 2012-01-31
> **canhoto said:**
> As for the screen problem, I still have it. I reset the pram several times, but nothing changed (which is weird). I also tried to use several xrandr commands. But each time I try the normal screen resolution for this monitor (1440x900), I loose one third of the desktop (like you see in the picture).
 
I'm running it with 1280x800, but... I loosed the clean and shinny look of my 1440x900 desktop...
 
I would have a go with the cvt command.  You can use it in conjunction with your xrandr command or put modelines in an xorg.conf as per the FAQ.   
 
Your lubuntu install - are you well below the 128GB limit?

---

### Post by canhoto on 2012-02-07
Well, it has been more than a week since I last updated this thread. Since then, I did the following:

- Tried to change the desktop manager (from kdm to gdm); I ended up with no dm at all. As I had this screen problem I couldn't work with the console (I can't see the whole commands). So I decided to reinstall everything. Fortunately, I had made backups.
- Several trials with triple-booting: Mac OS plus one Linux in the big drive, Linux in the other drive. Strangely, I managed to install Debian on the same drive than Mac OS and boot from it. But the X didn't start in Debian, although I had a desktop installed. I tried to install Ubuntu on that drive but it didn't work. 
- I tried to install 12.04 on both drives (each one at a time). From the big drive it didn't boot. From my current drive, first I choose the option to upgrade from the installed system (which was 10.10). But, after rebooting, I had two problems: the mouse cursor didn't move and, worse, the coulours of the screen and image were completely distorted. I don't know. May this is a bug? Anyway, I didn't go past the login screen.

- I tried to do a clean install of 12.04 (using the whole disk) and it didn't boot, I don't know why.

- Finally, I reinstalled Kubuntu 10.10. And I had my system back. Because it was a clean install and I wouldn't losse anything, I found the courage to upgrade to the most recent releases with their issues. The workarounds on the "Powe PC known issues" just worked. First, with 11.04, I just kept a cd in the drive to make it usable. I upgraded to 11.10 and I had the booting problem. I just ran the recommended command on the yaboot prompt and did the yabootconfig change and.. here I am with 11.10!
- But I was a bit disapointed with this version of Kubuntu. It's still a wonderful graphical environment. But there were some issues that seem not to be resolved, with no answers nor workarounds, like the one I talk about in[ this thread]("http://ubuntuforums.org/showthread.php?t=1920411"), which makes most of the apps unusable. So I ended up installing the other DE's, and I'm currently on Ubuntu, which has become quite nice, and with this option you have of choosing between Gnome 3 Shell, Classic Gnome or Unity. It just works and it's pretty.

BUT...

I still have the screen problem. I'm currently with 1280x800, which is ok. But my monitor can go up to 1440x900, and I had this resolution working fine before I began messing with Mac OS partitioning, installing several OS's, etc. I think it all begin there: when I reduced the size of the Mac OS partition and installed Debian.
Now, when I try the 1440x900, I have two thirds of the desktop, and two thirds of the screen filled (like in the picture). But, if I run Mac OS, I can have that resolution working perfectly.

So, although I can live with a 1280x800 resolution, if someone has an idea of how to solve this problem, I will appreciate.

---

### Post by summerkae on 2012-05-24
I am also having the screen resolution issue. It is only offering me the 1200x800 in both Ubuntu 12.04LTS and OSX lion.  I'm using an Apple Cinema Display 27" on a mactel G5 specifically Intel® Xeon(R) CPU 5150 @ 2.66GHz × 4 

my ubuntu has it's own HD, as does my OSX install. I have plenty of space on both HDs. I used refit to change the partitions and still use to choose the OS to boot into.  

I'm starting to suspect it's the refit program b/c it's happening in both OS for me.

---

