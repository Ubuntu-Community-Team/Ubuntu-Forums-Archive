---
title: "Quick, probably simple, noobish question"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by mattwinsatlife on 2007-12-14
My friend recently introduced me to Ubuntu by showing it to me on his own laptop. My PC desperately needs a better OS because ever since I got my MacBook, I hate Windows with such a passion. It's terrible, really.

I use my PC mainly for gaming. I play a lot of World of Warcraft and The Sims 2 on it, for example, and don't do much else with it. I've read about some programs/applications not being compatible with Ubuntu just because it's a Linux type system. So would I be able to use this OS with all my usual Windows games? 

And from what I read, it kind of just operates on top of my existing Windows XP or something? My buddy was running Ubuntu off a CD on a formerly Windows XP Toshiba laptop. I'm not really great with software lingo, so can someone explain this to me in simpler layman's terms?

---

### Post by -grubby on 2007-12-14
you can't use your old windows games with Ubuntu. You can try [WINE]("http://winehq.com") but it might take some configuring. Also, your friend who was running ubuntu on a CD was actually running a "[live-cd]("https://help.ubuntu.com/community/LiveCD")" which doesn't mess with hard drive unless you install it and then it no longer needs to be run from the CD.

---

### Post by diatribe on 2007-12-14
ubuntu does not run on top of windows it is an entirely different OS.  windows programs will not work under ubuntu.  some can be run through wine, there is a list at winehq.com

edit: after re-reading your post, do you even know what an OS is?

---

### Post by erfahren on 2007-12-14
there is a type of installation where Ubuntu can be installed within Windows with Wubi [http://wubi-installer.org/](http://wubi-installer.org/) - maybe that's what you're thinking of.

If you hate Windows but still find it necessary to have you can do what many of us do and look into going with a dual-boot setup. It's really not that difficult to do. I primarily use Linux but boot into Vista anytime I'm bored and want to spend 20 minutes seperately updating the OS and each individual program I have installed - lol (with Linux programs are updated together).

anyway, if you were unable to run your games using Wine you could keep Windows just for them and use Linux as your primary OS (it doesn't take up as much space as Windows).

--- just a thought

---

### Post by RomeReactor on 2007-12-14
Hi. Many windows games can be played in Ubuntu with the help of a program called **Wine** ([Wikipedia entry]("http://en.wikipedia.org/wiki/Wine_(software)"), [Official Site]("http://www.winehq.org/")), which is a compatibility layer between the instructions a windows game issues, and the Linux system running it. World of Warcraft [can be played in Ubuntu]("http://ubuntuforums.org/showthread.php?t=579378") using this program; unfortunately, The Sims 2 [does not work with Wine--yet]("http://appdb.winehq.org/appview.php?iAppId=1942"). Wine's progress is constant, but many view it as slow; you can see which games run using Wine in their [applications database]("http://appdb.winehq.org/"). These forums have a dedicated section for [gaming in Linux]("http://ubuntuforums.org/forumdisplay.php?f=93"), which means games natively running in Ubuntu, and a sub-section of that forum specially for [games played through Wine]("http://ubuntuforums.org/forumdisplay.php?f=313").

Hope this helps, and welcome to the forums!

---

### Post by mattwinsatlife on 2007-12-14
> **diatribe said:**
> ubuntu does not run on top of windows it is an entirely different OS.  windows programs will not work under ubuntu.  some can be run through wine, there is a list at winehq.com

edit: after re-reading your post, do you even know what an OS is?

Uh, nope. Told you, I'm no good at software or any computer stuff. Just going from what my buddy told me/showed me on his own laptop.

---

### Post by mattwinsatlife on 2007-12-14
> **RomeReactor said:**
> Hi. Many windows games can be played in Ubuntu with the help of a program called **Wine** ([Wikipedia entry]("http://en.wikipedia.org/wiki/Wine_(software)"), [Official Site]("http://www.winehq.org/")), which is a compatibility layer between the instructions a windows game issues, and the Linux system running it. World of Warcraft [can be played in Ubuntu]("http://ubuntuforums.org/showthread.php?t=579378") using this program; unfortunately, The Sims 2 [does not work with Wine--yet]("http://appdb.winehq.org/appview.php?iAppId=1942"). Wine's progress is constant, but many view it as slow; you can see which games run using Wine in their [applications database]("http://appdb.winehq.org/"). These forums have a dedicated section for [gaming in Linux]("http://ubuntuforums.org/forumdisplay.php?f=93"), which means games natively running in Ubuntu, and a sub-section of that forum specially for [games played through Wine]("http://ubuntuforums.org/forumdisplay.php?f=313").

Hope this helps, and welcome to the forums!

Thank you very very much! That was really helpful.

---

### Post by diatribe on 2007-12-14
> **mattwinsatlife said:**
> Uh, nope. Told you, I'm no good at software or any computer stuff. Just going from what my buddy told me/showed me on his own laptop.

jesus christ.

---

### Post by mattwinsatlife on 2007-12-14
> **erfahren said:**
> there is a type of installation where Ubuntu can be installed within Windows with Wubi [http://wubi-installer.org/](http://wubi-installer.org/) - maybe that's what you're thinking of.

If you hate Windows but still find it necessary to have you can do what many of us do and look into going with a dual-boot setup. It's really not that difficult to do. I primarily use Linux but boot into Vista anytime I'm bored and want to spend 20 minutes seperately updating the OS and each individual program I have installed - lol (with Linux programs are updated together).

anyway, if you were unable to run your games using Wine you could keep Windows just for them and use Linux as your primary OS (it doesn't take up as much space as Windows).

--- just a thought

And yes, I think that's what I heard. Because after having a Mac and seeing my friend's computer run on Ubuntu, I guess I kind of have an appreciation for nice user interfaces...if you understand what I mean.

My friend suggested Ubuntu because both of us have pretty old computers (about 3-4 years old) that just don't run Windows XP very well anymore. He said he got a huge improvement when he started running Ubuntu because it takes up less space and we both agreed it looks a lot better.

How can I get a dual boot? I know Macs can do it with Bootcamp, so I guess there's something for Windows or Ubuntu? What's it called?

---

### Post by RomeReactor on 2007-12-14
Can you give us more details about your PC? Like what processor does it have, how much memory (RAM), which video card?

Ubuntu uses a program called [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB") to dual boot.

---

### Post by mattwinsatlife on 2007-12-14
> **RomeReactor said:**
> Can you give us more details about your PC? Like what processor does it have, how much memory (RAM), which video card?

Ubuntu uses a program called [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB") to dual boot.

Pentium 4 processor (2.4 GHz I think)
ATI Radeon 1600x video card (256MB)
1 gig RAM

---

### Post by thelatinist on 2007-12-14
> **mattwinsatlife said:**
> Pentium 4 processor (2.4 GHz I think)
ATI Radeon 1600x video card (256MB)
1 gig RAM

Your PC will be just fine with Ubuntu.  You may have a little trouble with the ATI graphics card, but you should be able to get it working.  I've not had problems with mine.

As for dual booting, the Ubuntu Live CD has an installer right on the desktop which will take care of everything for you.

---

### Post by RomeReactor on 2007-12-15
> **mattwinsatlife said:**
> Pentium 4 processor (2.4 GHz I think)
ATI Radeon 1600x video card (256MB)
1 gig RAM

Your system looks to be more than adequate to run Ubuntu; to dual boot, you need to have windows installed first. That seems to be the case, so next you have to defragment windows at least twice to make sure it is compacted enough that no data is left in the space intended for Ubuntu. Next you [download Ubuntu from here]("http://www.ubuntu.com/getubuntu/download") (if you don't have it already) and then set your BIOS to boot from the CD drive. Depending on the motherboard your PC has, the method for entering BIOS varies; usually you press one of the function keys (F1, F2, etc) or press DEL as your system starts.

As you boot Ubuntu, it will run in what is called "Live CD" mode, meaning it will load entirely in your PC's RAM memory and will not write anything to your hard drive. I suggest you play with Ubuntu in Live CD mode for a while, to get to know the system.

When you feel you're ready to install it, press the "Install" button on the desktop, and that will start the installation process; you'll be guided step by step, and can go back to previous steps *before reaching the partitioner*, which will start to make a separate space in another filesystem format called EXT3 (windows uses NTFS). [This guide]("https://help.ubuntu.com/community/GraphicalInstall") can be of help.

---

