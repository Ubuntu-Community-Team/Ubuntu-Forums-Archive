---
title: "Ubuntu ppc issues vs. Ubuntu x86"
date: 2005-04-04
forum: Apple PPC Users
---

### Post by Emerpus on 2005-04-04
It has come to my attention that there seems to be a number things you can't do with Ubuntu/Linux ppc compared Ubuntu/Linux x86.  :neutral: 
Since I'm seriously considering getting a Mac mini and running Ubuntu on it I am trying to get a clearer picture of the exact disadvantages.

For me personally the largest disadvantage I have come across so far in the inability to use Skype. Apart from that I also know that there is poor driver support for e.g. Wifi, Bluetooth and printers.

Anything else I should know about?

And which printers *can* I use with Ubuntu ppc?

---

### Post by flange on 2005-04-04
Well, I'm fairly new to linux, but I run both ppc and x86 Ubuntu so I'll try to get this started...

First, there is no support for Airport Extreme.  Not sure what the Mini has, but if it's AE it's guaranteed to not work.  Sleep doesn't work either, at least not without some work that's more advanced than I want to deal with.

Second, you are limited to what's in the ubuntu repositories or compiling from source.  E.g., you can't d/l Firefox from Mozilla because the linux version is compiled for x86.  Also, the ubuntu-ppc repos do not have all the stuff that x86 has (open office 2 beta, for example).  That makes it a little more of a pain, but fortunately the ubuntu-ppc repos are still pretty good.

Third, if you want to dual boot, the ubuntu-ppc installer can't modify partition tables like the x86 installer.  You'll have to nuke your OSX install and repartition the drive with the OSX disk, then reinstall OSX, then install linux.  If you want to dual boot, do it soon after you get the Mac so you don't lose anything with wiping OSX.  Otherwise, the ubuntu-ppc installer is great.  It handles the yaboot stuff like a champ and makes the install process nearly as easy as the x86 install.

Fourth, once again a dual boot issue, some times Apple security updates destroy the yaboot boot loader and prevent you from booting into the linux partition.  It's probably fixable, but I didn't want to research it and ended up just reinstalling hoary because my linux home drive is a different partition and I wasn't going to lose much.

I don't ever print from my Mac (I have an iBook G4 1.2Ghz) or use bluetooth from linux, so I can't help there.

Hopefully someone else can add some of the more technical issues you might encounter.

Good luck.

---

### Post by poofyhairguy on 2005-04-04
[QUOTE=Emerpus]It has come to my attention that there seems to be a number things you can't do with Ubuntu/Linux ppc compared Ubuntu/Linux x86.  :neutral: 
Since I'm seriously considering getting a Mac mini and running Ubuntu on it I am trying to get a clearer picture of the exact disadvantages.
[/QUOTE]


Umm lets see:

Minimac support isn't 100% without some hacking on your part. Plenty of advice in the forums.

Window's Media Codecs can't be played because apprently x86 that one Debian repo that has it just guted them out of WMP. Since stuff from Windows won't run on a Mac,  Window's media files don't work. Its not bad, most of the other pluggins are there.

No Flash PLAYER FOR PPC LINUX! Macromedia won't make it. Biggest disadvantage. I dislike Flash, so its a plus for me. Free codecs can give you basic functionality (little difference for me).

---

### Post by daniels on 2005-04-04
Er, Bluetooth and printers should work just fine.  The main problems on PowerPC are wireless (since Apple/Broadcom refuse to provide a driver, or specs), and 3D acceleration (works with older ATI cards, doesn't work with any nVidia cards at all, or ATI Radeon 9550 or newer).

---

### Post by kris kincaid on 2005-04-05
I think you can use any printer on a PPC that you can on an x86. I have a Canon i560  and it took about 20 seconds to set it up.

Now connecting to my wireless network is killing me!  :?

---

### Post by usr3301 on 2005-04-05
[QUOTE=Emerpus]It has come to my attention that there seems to be a number things you can't do with Ubuntu/Linux ppc compared Ubuntu/Linux x86.  :neutral: 
Since I'm seriously considering getting a Mac mini and running Ubuntu on it I am trying to get a clearer picture of the exact disadvantages.

For me personally the largest disadvantage I have come across so far in the inability to use Skype. Apart from that I also know that there is poor driver support for e.g. Wifi, Bluetooth and printers.

Anything else I should know about?

And which printers *can* I use with Ubuntu ppc?[/QUOTE]
 Here is the VERY easy way to fix the missing yaboot screen.  There is no need to rebuild.
[http://www.yellowdoglinux.com/support/solutions/ydl_4.0/reset_boot.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_4.0/reset_boot.shtml)

---

### Post by Emerpus on 2005-04-05
Thank you for your input it is very helpful and I appreciate it.

If anyone can enlighten us even further please do.

---

### Post by Viro on 2005-04-06
No Java plug-ins either. These and Flash are useful for some websites like CNN which occasionally give you some useful Flash diagrams.

---

### Post by chascon on 2005-04-21
No java?
I've never noticed a problem with java.  Browsers such as mozilla give you a choice beteween using hava script and java, konquerer preferences always you to tie in directly to the java app.  Printing works about as fine as any cups printing.

And about not being able to resize OS X, sarge installer does this with parted?  and perhaps the d-i now.  You could do this from the buss card, which is a small download.

The disadvantages are:
1) no flash, not really there are some somewhat compatable opensource flash apps, but I don't like flash anyway.
The rea disadvantage:
2) no video acceleration if you have a nvidia card.  These predominate pb.  A lot of people buy these over ibooks thinking they are getting a better deal without realizing that nvidia's refusal to share specs creates opensource alternatives that do not make use of accel; nvidia do not make propietary pcc drivers either.  So you get a sluggish unresponsive machine.

Instead, get a ATI based machine.
3) As already noted, Airport extreme's refusal to co-operate with opensource community dispite that this is related to, I believe, a GPL based project.  This relates also to another company other than broadcom, that being Linksys.  Apprently and as I understand it (I don't speak for anyone or any organization), the arguement justifying not releasing teh entire code is that they did not have to release all the code because of dynamically vs. static implementation of modules.  Creative defense isn't it?  ... The kind of double talk one expects of lawyers.  My humble opinion is that if you benefit in anyway from gpl code, you are obligated to release your developments, unless you decide not to release it publically.  Stallman, author of gpl, has even said as much publically.

Don't take my word on the subject.  Read for yourself:

"On the same subject but on another front, the broadcom chipset used by apple 
for the airport extreme is also used in the Linksys WAP54G wifi access point 
... which runs under linux. This of course means there is a kernel module that 
drives the chip, and thus that either Linksys or Broadcom have code some 
driver for it. It makes me angry to think they would have gone that far and 
stopped there without considering their customers who care about running linux 
on their apple hardware."
[http://lists.debian.org/debian-powerpc/2004/02/msg00445.html](http://lists.debian.org/debian-powerpc/2004/02/msg00445.html)

On the failure to produce a fullyworking kernel read:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html)

There's more out there on the subject, just a little hard to find for some reason.

---

### Post by slux on 2005-04-21
All the things that are lacking on PPC are the result of non-free binary-only software that is only compiled for Linux x86.

As far as I'm concerned these are problems on x86 too but as they don't cause an immediate inconvenience, you may not feel that way.

On the topic of acceleration (3D or otherwise), I think the xorg "nv" 2d-only driver is still usable enough (even the proprietary ones do not enable 2D rendering acceleration by default) and if you're using an ATI card (<= 9250) like on most new Apple laptops, even 3D acceleration is provided by the excellent DRI project. Not that it matters so much, though. Linux games are relatively few and on ppc the list is greatly reduced as far as proprietary ones go: UT/Doom 3/Enemy territory etc. are not available, some titles from LGP are. All free software games can still be played of course.

I don't see the driver thing as a big issue vs. x86. You shouldn't really be relying on hacks like ndiswrapper on closed drivers that can go away any time anyway and usually there are free options so if you do the research you won't be bitten by it.

The two largest problems are lack of Flash and the inability to use win32 video codecs in apps such as mplayer - you're stuck with what the app can play back natively so at least some quicktime and windows media clips can't be played. 
You can't use wine to execute windows binaries either.

Flash doesn't bother me much personally since it's mostly useless anyway and a non-standard web feature.

---

### Post by xet7 on 2005-04-21
Huh, no Java and Java plugin? Doesn't anything with this thread work? :
[http://www.ubuntuforums.org/showthread.php?t=28303](http://www.ubuntuforums.org/showthread.php?t=28303)

---

