---
title: "Ubuntu 7.10 PPC Desktop"
date: 2007-11-05
forum: Apple PPC Users
---

### Post by caladan1810 on 2007-11-05
Hi Everyone,

I'm Using an iMac G4 Flat Screen, I can boot the Live CD but I cannot install from the Live CD
anyone else having probs trying to install.

Any Assistance would be greatly appreciated.

Cal.:KS

---

### Post by iAtari on 2007-11-05
Welcome to Ubuntu Forums.

If you could lend us some basic system specs, (RAM, Processor Speed) it would be appreciated.

Depending on your speeds, you might want to consider 6.06 if 7.10 doesn't work. Also, try the alternate installer .iso, it uses less memory to install and is much quicker than booting off the live CD. This would be my recommendation.

Any other problems, unsolved issues, ect, feel free to ask.

Good luck.

iAtari

---

### Post by ppc_guy on 2007-11-05
I would agree with what the previous poster.. As a long time ppc user ( sense hoary hedgehog ) Need a bit more info. Just be glad it's a new world machine and you don't have to worry about bootx! 
But something I would do first.. Boot into X and md5 your iso.. Make sure it's a good burn. In my experiance macs can be finacky on iso's.

~Nathan
-----------------------------------------------------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel
-----------------------------------------------------------------------------------------------------------------

---

### Post by caladan1810 on 2007-11-05
Hi Guys,
Systems Specs:

iMac G4 800MHz
768 MB RAM
80 GB HDD
Pioneer DVD-R 16X

Currently Has Mac OS X 10.4.10 Installed.

Hope this helps thanks you for your quick responses :)

---

### Post by BladeMelbourne on 2007-11-05
Hey Cal,

What powers your display? (eg my Mac Mini has a Radeon 9200)

What does "I can boot the Live CD but I cannot install from the Live CD" mean? How do you know the install process dies? White or black screen, hard disk issue? What is the last step that the installation process gets up to?

I'm running Gutsy OK, but with an ati radeon driver from early Feisty.

-- BladeMelbourne --

---

### Post by caladan1810 on 2007-11-05
Hi Blade,

I said I can boot the Live CD but not install from it . It boots to where I get the 
Yaboot Menu and that's as far I can get. I have tried other methods such as
live-nosplash-powerpc video=ofonly

this then gets me to another menu where I input

modprobe ide_core
modprobe ide_disk
modprobe ide_cd
exit

But I still get nothing I'm left with a with screen and pink text.

---

### Post by Kevsta100 on 2007-11-05
> **caladan1810 said:**
> Hi Everyone,

I'm Using an iMac G4 Flat Screen, I can boot the Live CD but I cannot install from the Live CD
anyone else having probs trying to install.

Any Assistance would be greatly appreciated.

Cal.:KS


On the little info provided it seems we had a similar problem.
I fixed the install process by manually mounting and setting up my partions during install.


If ya already did that and it still fails leave a lil more info, I'm a newb myself and on a PC, 
but maybe someone will see and drop in a solution.

I'll suggest what I can as I know how frustrating it is, but don't expect to much as am just learning along the way.

---

### Post by frog_pilot on 2007-11-05
Maybe the ati-display-driver dosn't recognize, your video-card.

Install from edgy or feisty alternate-cd.

Do not take gutsy, because it's ppc-version isn't that stable.

If X-server starts with an error, try to add the line ```
Option   "NoInt10"   "yes"
``` to the drivers-section of your xorg.conf

Be aware that you have to be root, to alter this file. With```
sudo nano /etc/X11/xorg.conf
``` you can access the file writable.

---

### Post by king_arthur on 2007-12-19
Same problem here.

Gutsy PPC booting allright using the live-nosplash-powerpc video=ofonly trick on my iBook G4.

On the iMac G4 (flat panel) I get stuck at the busy-box.

The modprobe core-ide trick doesn't get me out of this situation.
Exiting the busy-box returns various errors.

break=top doesn't help either.

This is a significant regression as older powerpc live-cd's have always been working on the very same machine.

Actually, I found it rather incredible that such a buggy release was made with Gutsy, there must be an obvious problem with some Q.A. procedures as a major bug was acknowledged by several developers, including Benjamin Herrenschmidt, but found it's way into the final release. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337)

:(

/P

---

### Post by ubuntubrian on 2007-12-19
I used:

live-nosplash-powerpc video=ofonly break=top

Then:

modprobe ide-core
exit


Gutsy Live CD booted for the first time. Manually st my wifi in "Administration>Network" and I'm running. No sound as far as I can tell but since no media player will play I can't test it. Stuff freezes alot and requires "force quit". Wobbly windows are cool, graphics better all around but I want F-spot and Evince plus sound.

---

