---
title: "Need Windows Simulator or Emulator"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-07-10
Even though I am slowly switching all my PC functions over to Ubuntu, I will still need Windows to run some programs.  Specifically, I need Windows to run Turbotax during tax season.

Does anyone know the best way to run Turbotax (or any programs that work only under Windows) within Ubuntu?  Should I download VMWare, or Wine, or buy Crossover Weavers, or something else?

If I use VMWare, do I actually have to take my Windows XP CD and load it into Ubuntu through VMWare?

I'm new to Linux (6 months or so) and really want to give Linux a fighting chance!

Thanks in advance.

---

### Post by Malibu Illusion on 2007-07-10
Looking at the [database entry](http://appdb.winehq.org/appview.php?iAppId=623) for that particular program, it would seem to me like people are not having too much luck with it on the WINE platform.  I'd suggest running a virtual machine to attempt to run it and yes, you'll be needing your installation disc.

---

### Post by benjamin1254 on 2007-07-10
simple answer use VMWare and install xp through a virtual machine... that will work if only you have enough system power. Not enough power and your system while emulatingwindows will become a graphical brick!

---

### Post by gigaferz on 2007-07-10
hey guys!

my winxp installation disc, is one of those 5  cd set to install or reinstall windows, can i run them to install xp in vmware or it has to be a single disc (oem or retail)?

there was no xp installation just an extra partition and i made that cd set, i did that to get more room  for linux

---

### Post by linux_kid on 2007-07-10
Do you currently Have Windows XP installed on your PC?  If so, Use VMware's Converter ([click here]("http://www.vmware.com/products/converter/")).  I advise you have at least 1GB of memory, because I needed to run at 600x800 on 512MB to get anywhere.

---

### Post by gigaferz on 2007-07-10
sweet!

---

### Post by mactece on 2007-07-10
out of interest if you need 512k to run it what speed does your cpu run at. Mine uses a system of mice and carrier pigeons by way of comparison but has 1gb of ram to support it.

---

### Post by Raineer on 2007-07-10
If you focus on only running windows and not trying to multitask heavily with Ubuntu, it doesn't take a terrible amount of CPU power. 2ghz should be decent, it's just your performance won't be overwhelming but it will run TurboTax.

---

### Post by anewguy on 2007-07-11
> **gigaferz said:**
> hey guys!

my winxp installation disc, is one of those 5  cd set to install or reinstall windows, can i run them to install xp in vmware or it has to be a single disc (oem or retail)?

there was no xp installation just an extra partition and i made that cd set, i did that to get more room  for linux

Yes you can use the recovery disks.  I made a virtual disk using VMWare server using the recovery disks on my Gateway laptop.  The main things I had to were:

(1) After VMWare creates the virtual machine, but before you run it, go into the .vmx file and change the line that says scsi.... to false.  This avoids (for me, I don't know about others) stops me from having the startup stop after it puts a white bar across the screen. 

(2) For my touchpad to work I had to change the mouse lines to type ps2.

(3) Once you get booted be sure to install the vmware tools.


Hope it helps.:)

---

### Post by Rossiter on 2007-07-12
I'm new to this also, but an easy solution may be to just use TurboTax Online.   [[https://turbotaxweb.turbotaxonline.intuit.com]]("https://turbotaxweb.turbotaxonline.intuit.com%5D")  It won't matter which O/S you are using, so long as you have a functional browser.  I made the the switch from Desktop TurboTax to the online version a couple of years ago and have not regretted the move.

If your are not interested in that approach, then the following may be of interest to you...
I have been looking at several threads regarding the use of Quicken (also an Intuit product) in Ubuntu by running it under Wine.  It seems that many have done this successfully and I will be attempting it myself very shortly.

If I can get it to work also, I will finally be freed from Bill Gates forever.
-----------------------------
I tried wine and found it to be a great disappointment.  Quicken will run but is quite buggy and online features were not functional.

---

### Post by Malac on 2007-07-12
Have you tried VirtualBox by InnoTek it's free and comes in an Ubuntu deb file that you can install easily.
Downloadable from InnoTek Web site: [http://www.virtualbox.org/](http://www.virtualbox.org/)
Or there are instructions for adding it to your repositories list.

Hope this helps.

---

### Post by Malibu Illusion on 2007-07-12
A Windows Simulator you say?  Sure, there's one [right here](http://www.computerpranks.com/download/programs/fun/windows_rg.swf). =^^=

[On a serious note, I've used VMWare Server to emulate Windows environments in the past and it works well.]

---

### Post by F_r_e_d on 2007-07-12
I'm a little leary of doing my taxes on line.

Does anyone have any experience running Turbo Tax in VMWare?

---

### Post by anewguy on 2007-07-15
I haven't used Turbo Tax in VMware, but if it will run in Windows, it will run in VMware (some games, etc., won't run well if at all, but Turbo Tax should run fine).  If you want to print, etc., be sure you have your printer working in Linux first.

Please let us know how things go!:)

---

### Post by machoo02 on 2007-07-15
> **Malibu Illusion said:**
> A Windows Simulator you say?  Sure, there's one [right here](http://www.computerpranks.com/download/programs/fun/windows_rg.swf)

HA!  Love it!

---

