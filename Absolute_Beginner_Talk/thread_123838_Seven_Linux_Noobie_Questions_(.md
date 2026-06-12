---
title: "Seven Linux Noobie Questions :("
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by wilsonisme on 2006-01-31
Okay I have used linux a few times, set up a box with ubuntu, but did not use it heavily, it was more of a "hey this could be fun" kind of idea. 
Anyway, I am thinking about using it more seriously now, but have a few questions.

1) Video Codecs: Are all the ones that someone might need available for linux? Such as divx, xvid, etc. I remember just getting MP3's to run on linux was a quasi pain, so im a little scared videos will be a huge pain in the rear. What about .movs, .wmvs?

2) Are there any really good video plug-in's for firefox in linux? I remember I tried mplayer's and it totally sucked, didnt even work with most videos.

3) Does anyone have a link to a really good console tutorial? Like with common commands that you need a lot, etc.

4) I have a wireless LAN setup at my house, just a POS netgear wireless router but it gets the job done. On my windows 2k pro box upstairs, I am able to print to a printer that is connected to a computer two floors under me (using the "share this printer" function in xp which turns it a print server) Would I be able to do this with ubuntu? Or would it be yet another project that unfourtantly is oh so easy to do in windows but would require hours of painstaking research to maybe acomplish in linux? :(

5) Would there be any way to get Guild Wars running in linux with Wine or something similar?

6) The computer I am thinking of putting ubuntu on is quite expensive. Would it's performance be wasted on linux because of generic video drivers linux would use for example? Also if I got guild wars running in linux, would it's performance suck because it is being run in Wine or whatever?

7) If I back up my whole hard disk with Nortan ghost, (I have done this before no problem) would installing linux cause some complication that would prevent me from restoring the computer back to it's pre linux state? (like would grub bootloader or something screw it up) Also, anyone know if I could use ghost to back up the linux system?

That is it for now, thank you very much in advance! :)

---

### Post by wilsonisme on 2006-01-31
Oh also, quasi unrelated, I just tried booting off the live CD on this system I was thinking about installing ubuntu on, and everything goes fine until the ubuntu loading screen finishes, then all I get is a discolored unrecognizeable mess vertical lines on the screen to break up the garbage. I have a nvidia 6600 GT card in the computer. Any idea whats goings on?

---

### Post by frodon on 2006-01-31
For codecs, firefox plugins, ... i advice you to run automatix : [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
For the other questions, just use the search field of the forum and you will find what you are looking for.
6) No if you have an nvidia card.
7) I use norton ghost to backup my linux partition and it works really well, only the latest version offers ext3 support (the ubuntu file system).

Look to the link in my signature you will find a lot of informations in.

---

### Post by Madpilot on 2006-01-31
[QUOTE=wilsonisme]1) Video Codecs: Are all the ones that someone might need available for linux? Such as divx, xvid, etc. I remember just getting MP3's to run on linux was a quasi pain, so im a little scared videos will be a huge pain in the rear. What about .movs, .wmvs?
[/quote]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) - specifically, look for the "Codecs" section for the w32codecs.

> 
2) Are there any really good video plug-in's for firefox in linux? I remember I tried mplayer's and it totally sucked, didnt even work with most videos.


Not sure, actually.
> 
3) Does anyone have a link to a really good console tutorial? Like with common commands that you need a lot, etc.


[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)

I'll leave the wireless & Wine questions for someone else, I don't run either!

---

### Post by frodon on 2006-01-31
2) If you don't like the mplayer plugin, try the media player connectivity extension of firefox, it just open the stream with the player you want (it's the one i use).

---

### Post by hen3rz on 2006-01-31
> 3) Does anyone have a link to a really good console tutorial? Like with common commands that you need a lot, etc.

This tutorial is great. It taught me all i know:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by linuxden on 2006-01-31
[QUOTE=wilsonisme]3) Does anyone have a link to a really good console tutorial? Like with common commands that you need a lot, etc.[/QUOTE]

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

I have found this to be the most comprehensive how to... Its fun and you go on an adventure... Its cool

---

### Post by Edward The Bonobo on 2006-01-31
Console tutorial:

[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php) 

It's easy to follow and written in nice, folksy language without being too patronising.

---

### Post by Edward The Bonobo on 2006-01-31
Ah...my link was the same pages as the linux.org one.

---

### Post by Who on 2006-01-31
> 1) Video Codecs: Are all the ones that someone might need available for linux? Such as divx, xvid, etc. I remember just getting MP3's to run on linux was a quasi pain, so im a little scared videos will be a huge pain in the rear. What about .movs, .wmvs?

The reason things like codecs are difficult with Linux is more because of copyright/legal issues than software availability. A lot of work is being done at the moment on making it easy for people who don't live in a police state ( ;) ) to get hold of the software

Check out EasyBreezy or Automatic - they help you install a whole bunch of software. 
Also see the PLF (Penguin Liberation Front)


> 2) Are there any really good video plug-in's for firefox in linux? I remember I tried mplayer's and it totally sucked, didnt even work with most videos.

I have no trouble with RealAudio on Linux (using Realplayer - thanks to the BBC leaning heavily on Real to make it's base OS) so you may have luck with RealVideo. EasyBreezy installs a bunch of firefox plugins - I never watch video in the browser window I normall download it. (note also that I can use IE6 under Wine - though I have no ieda about what codecs are available)

> 4) I have a wireless LAN setup at my house, just a POS netgear wireless router but it gets the job done. On my windows 2k pro box upstairs, I am able to print to a printer that is connected to a computer two floors under me (using the "share this printer" function in xp which turns it a print server) Would I be able to do this with ubuntu? Or would it be yet another project that unfourtantly is oh so easy to do in windows but would require hours of painstaking research to maybe acomplish in linux? :(

Simple answer: It _shouldn't_ be a big project. The toool required is called Samba and as far as sharing Windows folders goes it is excellent.

Just a note about things taking hours: often that can be the case if you try and sort it out alone - I find constructive use of Google can really cut problem solving times. I won't pretent Linux doesn't have heaps of idosyncracies, but they are often well documented :)

> 5) Would there be any way to get Guild Wars running in linux with Wine or something similar?

[http://appdb.winehq.org/appview.php?versionId=3251](http://appdb.winehq.org/appview.php?versionId=3251)
Things are looking up :) it seems with wine 0.96 it works...

Note: you'll have to add the Wine repositories to Synaptic to get 0.96
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

> 
6) The computer I am thinking of putting ubuntu on is quite expensive. Would it's performance be wasted on linux because of generic video drivers linux would use for example? Also if I got guild wars running in linux, would it's performance suck because it is being run in Wine or whatever?

Basically, no. Linux offers you way more opportunity to graphically display your processor/pc prowess with eye candy :P

There are some benchmarks of Wine here
[http://wiki.winehq.org/BenchMark-0.9.5](http://wiki.winehq.org/BenchMark-0.9.5)

For NATIVE games, anything not runnig in Wine, the performance will  not be wasted. ATI and nVidia both have drivers _specifically_ for Linux - so that isn't much of an issue :) - they aren't _quite_ as good as the Windows counterparts, but they're pretty good

> 7) If I back up my whole hard disk with Nortan ghost, (I have done this before no problem) would installing linux cause some complication that would prevent me from restoring the computer back to it's pre linux state? (like would grub bootloader or something screw it up) Also, anyone know if I could use ghost to back up the linux system?

I think you can choose to install Grub somwhere other than the MBR. I think it also saves the bootloader that was there and you can restore it - but I don't _know_ that for sure. I mess about with my PC on a regular basis and I find that you can usually get the MBR back using the boot cd of the OS you are using...

Good luck! hope you stick around :)

---

### Post by wilsonisme on 2006-01-31
Thank you VERY much for all the great responses guys! About my card problem, it sounds like im going to have to manually install the drivers from the command line before Gnome will work? Would anyone happen to know of a link to a walk through of this?

Thanks again :mrgreen:

---

### Post by Who on 2006-01-31
I don't really know what's going on :P BUT I do know that installing the official nvidia drivers is a simple as adding some repositories and installing some packages (With Linux, typically, all the softwareis packaged by the distribution vendor and rather than having installers etc you just install the package and the 'package manager' installs everything it needs to make it work!). This is very easy to do from the command line...

Method 1 froim this howto says it all :)
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

