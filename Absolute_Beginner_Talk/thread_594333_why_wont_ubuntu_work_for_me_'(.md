---
title: "why wont ubuntu work for me? :'("
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by munnyman5 on 2007-10-27
I recently bought a laptop, specifically, an Acer Aspire 5920G (sometimes known as the Acer Aspire 5920-6313 ?) notebook, and my first thought was to get Ubuntu on it.

Sadly, though, when I tried to do so (by changing the boot properties to check the DVD drive first, then the HDD) it didn't work. I had my ubuntu 7.04 distro CD in there, and it went to the screen, you know, with the UBUNTU in orange across the top and the "Run or Install Ubuntu" etc. selection of things to do under it. I chose the aforementioned Run or Install Ubuntu command, and it went thorugh the plethora of lines of what appeared to be code (but which could just as well be chinese, because I know nothing about programming... oh, and I don't know how to read chinese). Then, instead of getting the black screen followed by the friendly ubuntu boot-up screen (rectangle, showing what was being loaded underneath) and the the Ubuntu desktop, all I got was something like "could not access tty" or "could not run tty" then it told me to type "help" into some sort of possibly-chinese command prompt which caused me to promptly go into a state of complete neural shock. I did, however, pull it together and type "help", and it told me then that i could type this s***load of stuff into the prompt, but didnt tell me what each one would do! SO then i tried "exit" which was not there. The next closest command on the help list was "kill", and so help me god, i would NOT type that into anything on my new laptop. So then i turned it off and rebooted, quickly ejecting the drive before it started the ubuntu cycle again. Ever since, I have been looking for help across the vast tubes of the internet. I hope my search ends here.

 Thanks in advance.

---

### Post by Orbital75 on 2007-10-27
Most of the time it's the Graphics card that causes issue, I'd try using
Safe Graphics Mode.... If that doesn't work, Give the alternative CD a try,
that may help.

---

### Post by llamakc on 2007-10-27
Try installing in Safe Graphics mode first. Perhaps its the noapic issue?

---

### Post by w7kmc on 2007-10-27
Does your lappy have the nvidia 8600MGT card...perhaps this link may help:

[https://answers.launchpad.net/ubuntu/+question/13983](https://answers.launchpad.net/ubuntu/+question/13983)

Sounds like the Xserver did not start.  You may need to try the 'alternative CD'  

Search around the boards for any workarounds for your graphics card type...

---

### Post by munnyman5 on 2007-10-28
OK... Uh, yeah my lappy (lappy 486? Homestarrunner.com? Anybody?) has the 8600m GT 256mb graphics card. Do you guys think that maybe using version 7.10 will make a difference? Because I can download and burn that disk no problem. I just want to be sure that it will work. I dont see any workarounds for the 8600.. maybe I'm inept at studying for Literature tests and searching Ubuntu Forums at the same time. I dunno. Uh, so safe graphics mode? If I do that, will it work if I boot ubuntu from the HDD in non-safe-graphics mode? Also, some guy with the same gpu as me did the alternative CD thing, and said that when he tried to boot from the hdd after installing, he got some error, and it still wouldn't work.

So yeah. Am I totally screwed? I really wanted ubuntu...

:confused:

---

### Post by errenay on 2007-10-30
There were problems with Acer Aspire 5920 & (K)ubuntu 7.04. But the main reason was not the graphics card, but drives. To install (K)ubuntu try version 7.10 LiveCD. If this does not work, try alternate CD.
These links may be useful:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920)
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920G](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920G)
If (after installation) there are some problems with X (no "windows") you may always go to console mode (Ctrl+Alt+F1) and change the driver in xorg.conf (from "nv" or "nvidia" to "vesa").
For me the binary drivers from restricted manager works without any problems.

---

### Post by Netrunner on 2007-12-14
> **munnyman5 said:**
> I recently bought a laptop, specifically, an Acer Aspire 5920G (sometimes known as the Acer Aspire 5920-6313 ?) notebook, and my first thought was to get Ubuntu on it.

in acer aspire 5920g (and other santa rosa i guess)
if you do not want vista but linux
access bios (f2 if i remeber well)
choose verbose startup
choose order of device you want to boot and enable the press f12 (or f6 i can't remember) to choose wich device you use to boot, (now when you power on pc and press f12 or f6 you can choose from the list of available boot drivers)
exit bios and restart
now take a read here and go on
[http://ubuntuforums.org/showthread.php?t=635888&highlight=acer+aspire+5920g](http://ubuntuforums.org/showthread.php?t=635888&highlight=acer+aspire+5920g)
choose your distro (for me ubuntu gutsy or sidux worked well) and make an install cd.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
boot from cd and instal in console mode (not necessary with gutsy, but you have to wait untill vesa start).
choose language, partitions, and so on.
finish installation.

if you want, you can immediately install[ NVIDIA ]("http://www.nvidia.com/Download/index.aspx?lang=en-us")drivers to fix resolution and avoid vesa or nv. 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)
if a problem occour simply ask.
[i still haven't made the integrated modem work but i'm very happy of my laptop]("http://ubuntuforums.org/showthread.php?t=601887&highlight=acer+aspire+5920g")


you can also install 7.04 but i suggest do do it from console and compile a new kernel for it, gutsy installation is easyer if you come from windows.

---

### Post by Bartender on 2007-12-15
I also just bought an Acer 5920.  From what I've found there were several problems with 7.04.  7.10 much better.  Not sure if all problems went away but better.
I think I'll try using an alt install CD, too - have heard hints of problems with the LiveCD's.

---

