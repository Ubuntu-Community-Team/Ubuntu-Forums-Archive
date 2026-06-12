---
title: "xubuntu: what version is still compatible with oldworld?"
date: 2007-02-01
forum: Apple PPC Users
---

### Post by pixeldotz on 2007-02-01
this is a crosspost from the GENERAL HELP forums. they where able to help me over there but suggested i post here aswell for more info.

i've been using xubuntu for awhile now on a 1GHz laptop and simply love it. the simplicity it brings to a linux distro is incredible.

my questions is this, i have an old powerbook3400c that was given to me that runs very nicely (reads burned cds and all) under macos 8.6.

i tried installing ubuntu 5.10 on it and it installs completely without hassle. when i get to the login screen passed the startup sound (using x of course) the screen is all messed up with tons of snow everywhere, then after a few seconds it looks like an old tv with rabbit ear antennas and a magnet sitting on top.

i know x supports this lcd because i was able (and am currently typing this) from a yellowdog 3.0 install on this powerbook (i'd much rather have xubuntu).

after the rant, that is my main question, what version of xubuntu can i install on this and will i still have the same problems as as i did with ubuntu and the xserver?

fyi: i prefer xubuntu as it's what i'm most familiar with and the flexibility is awesome compared to yellowdog (imo of course).

---

### Post by 3rdalbum on 2007-02-01
Xorg is probably misconfiguring the display on Xubuntu. Why not take your xorg.conf file from Yellowdog and note down its settings, then put them into Xubuntu?

---

### Post by Tommy on 2007-02-21
> **pixeldotz said:**
> i have an old powerbook3400c ...

i tried installing ubuntu 5.10 on it and it installs completely without hassle. when i get to the login screen passed the startup sound (using x of course) the screen is all messed up with tons of snow everywhere, then after a few seconds it looks like an old tv with rabbit ear antennas and a magnet sitting on top.


On most of the oldworlds you have to pass a kernel parameter to get the video working properly. You put it in the kernel field in Bootx, in the same place where you put your root= parameter. It will start with video= and have some gibberish that will be specific to your hardware. For example, video=atyfb:vmode:18,cmode:24 is an example for some models. Google your model and see what you can find. (Actually, since you've been using linux for awhile you probably know all this!!!)

I've been using ubuntu for YEARS on my PowerBook G3 Series- Wallstreet II/PDQ, but I've been upgrading since Warty -- unfortunately many of the releases simply won't install from scratch. It's running Dapper now, but I have been unsure whether I should make the leap to Edgy, since the upgrade to Dapper was slow and painful.

I have a GOOD story, however -- I have a PowerMac 9600 (MUCH larger in size than our PowerBooks ;-) ) that I have been trying to put linux on for years. If it wasn't one thing it was another. Well the other day I decided to try again, starting with Dapper. No go. I tried ALL the variations of the PPC disks for 6.06 and none would boot it. I also tried both of the 2006 releases of Gentoo. Same problem. The kernel gave up with an obscure error.

Then I tried the Edgy Alternate 6.10 disk -- Edgy boots GREAT on that machine, and it will work with no kernel parameters (which is the same as video=ofonly) as a stopgap until you find the actual video parameters you need. (ofonly is a very slow driver but it works.) [OH and anyone else trying this on a 9600 will want to know that I have NOT yet tried using the video card that comes a 9600. What a nightmare under linux!]

You may run into a few kinks with the installer because things like SCSI drives aren't common on PPC anymore and fewer of us oldworld folks are even trying nowadays. Plus you may have to add some modules to your /etc/module file to get things like the printer port and modem working. But in my experience, Edgy is great, Dapper is a no-go.

---

### Post by oswaldkelso on 2007-02-23
I dont know what xfce version will work but this [link]("http://www.rockhopper.dk/linux/hardware/powerbook-3400.html") show howto fo Gentoo so my help you get going

also you'l get bootloaders [here ]("http://penguinppc.org/bootloaders/") bootx is the one you need

---

### Post by ballen12 on 2007-03-15
i've been looking around the forums quite a bit and can't find much...  i just bought a powerbook 3400c with the 240Mhz proc and 144M of RAM for $50 and thought it would be awesome to run ubuntu or xubuntu on it.  however, i can not for the life of me get it to boot to the ubuntu or xubuntu cd.  can anyone offer any advice or point me in the right direction?

---

### Post by grazie on 2007-03-15
ballen12,

You have an old world Mac which isn't directly supported by Ubunutu. All this means is that ubuntu cd will not boot directly. Search the forums for 'old world' and bootx. You should have started a new thread really. :)

---

### Post by Tommy on 2007-03-18
> **ballen12 said:**
> i've been looking around the forums quite a bit and can't find much...  i just bought a powerbook 3400c with the 240Mhz proc and 144M of RAM for $50 and thought it would be awesome to run ubuntu or xubuntu on it.  however, i can not for the life of me get it to boot to the ubuntu or xubuntu cd.

As grazie wrote, you will need to learn the arcane mysteries of bootx, which is a Mac OS 9 program that boots linux.

I just did a google search and found this thread about a successfull 3400c install:

[http://ubuntuforums.org/showthread.php?t=351956](http://ubuntuforums.org/showthread.php?t=351956)

P.S.: The wiki page with the oldworld information has gotten really messy over time but it has essential information on it. [https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by ballen12 on 2007-03-18
yeah i've managed to get bootx working but i haven't been able to successfully start the ubuntu install.. i'll check out the links you posted and keep at it.  basically, as soon as it kicks me out of OS 9 and into the install the screen is all scrambled and you can't read it.  thanks for the links.

---

### Post by ballen12 on 2007-03-18
so from everything i'm reading it looks like there is absolutely to run JUST linux on an oldworld mac.  you have to boot into OS 9 first then click the linux button in bootx to run linux.  am i correct?  if so, that sucks.

---

### Post by Tommy on 2007-03-19
When the screen goes scrambled that probably means you need to figure out what video parameters to pass to the kernel. I haven't been able to find them for your model... but I don't know where to look anymore... the pages I used to look for seem to be down. There used to be a chart somewhere with the parameters for all the models known to run linux.

Try adding this to the boot parameters in bootx:

video=ofonly

AND/OR you may need to use the alternate install CD which has a non-graphical installer. The video=ofonly parameter may get you through the install but it will be much slower than finding the correct setting for your screen hardware.

And yes, you CAN ditch the Apple boot process using Quik or bootfloppies, but those processes are apparently so buggy and difficult to configure that most give up on them. Having a "classic" Mac boot partitioin with bootx is so much easier, I hear. Apple never released the code necessary to boot another OS on their hardware. You can personally make a bootable CD for oldworlds but in practice Apple controls all the necessary code so nobody can distribute it.  Bootx gets around this problem.

---

### Post by ballen12 on 2007-03-19
alright fine, i accept the fact that I can't run JUST linux (because it's hard enough getting it on there let alone trying to use Quik) so I'll try again tonight maybe.  I've downloaded the Xubuntu alternate cd so i'll try that...

---

### Post by Tommy on 2007-03-19
> **ballen12 said:**
> alright fine, i accept the fact that I can't run JUST linux (because it's hard enough getting it on there let alone trying to use Quik) so I'll try again tonight maybe.  I've downloaded the Xubuntu alternate cd so i'll try that...

Now I can't remember if anyone has mentioned this livejournal posting that documents in explicit detail how someone got Ubuntu running on his PowerBook 3400c -- but the posting is more than a year old and the installer & kernels have changed a lot since then. 

[http://fare.livejournal.com/93274.html](http://fare.livejournal.com/93274.html)

(This guy compiled a custom kernel to avoid a showstopper, so it might not help you all the way.)

I believe the Alternate CD has the non-graphical installer available so you'll know whether the install is working without having to mess with X.

---

### Post by SubGothius on 2007-05-17
[Looky here for detailed instructions on how I installed Xubuntu 6.10 Edgy on my OldWorld PowerMac clone](http://ubuntuforums.org/showthread.php?p=2419715#post2419715) (a Umax S900 dual-200MHz 604e with onboard SCSI and an ixMicro/IMS TwinTurbo video card same/similar as what Apple provided in the 9500/9600).

Although you initially will need to have MacOS installed (even just a bare-minimum System taking up a few-hundred MB partition, maybe even less) in order to use the Old World [BootX bootloader](http://penguinppc.org/bootloaders/bootx/) to boot into the installer, once you have Edgy installed, you *should* be able (tho' I have not attempted this myself... yet ;) ) to install the [quik bootloader](http://penguinppc.org/bootloaders/quik/) (run "aptitude install quik") and configure your Open Firmware to boot into Edgy as your default OS; after that point, the MacOS partition is vestigial (but may be handy to keep intact for recovery/repair or "nuke'n'pave" clean reinstalls).

I did finally iron out the last few issues I mentioned in my install post (follow links to spinoff threads for details), although my text-only console display remained all-black-on-black during boot and jittery/distorted otherwise.  The Feisty kernel resolved those console text-display issues and otherwise seemed to detect my hardware impressively well, but [Feisty also introduced far more perturbing issues re: SCSI drive detection](http://ubuntuforums.org/showthread.php?t=440592) (it can only access one drive out of 3 hard drives and 2 CD drives on the bus!); therefore, whilst I managed to get Feisty installed on that one disk to where it seems to be performing well enough for basic uses (seems faster than Edgy as well), I am still limited to using only one drive and left with Nagging Doubts about its long-term viability, so I may soon be doing a nuke'n'pave to get back to Edgy, unless some fix or workaround for my lingering issues with Feisty should magically appear before I get around to downgrading.

---

