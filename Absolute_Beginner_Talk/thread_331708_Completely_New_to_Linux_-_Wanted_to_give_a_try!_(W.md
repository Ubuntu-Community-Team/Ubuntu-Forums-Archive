---
title: "Completely New to Linux - Wanted to give a try! (Wireless Issue)"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by guyatwork37 on 2007-01-04
So I am brand new to Linux, but I have been curious to try it for awhile.   So I did my research and really liked the Ubuntu community as well as everything it had to offer.  Now I want to get my hands dirty.

I installed Dapper on my laptop (Compaq Presario - fairly old).  I have it up and running but I'm not too sure where to go next.  I figured getting my internet working would be clutch.  So I plugged in a network card as well as a USB stick but neither is detected.  No biggie I figured as much.  I did some research and found that I needed ndiswrapper to get it running.  Now this is where the problem begins.

I downloaded ndiswrapper from sourceforge and put it on the laptop and ran the following in the terminal:

 # tar -xzf ndiswrapper-1.33.tar.gz

but it gave me an error the first time i fired it up.   That was last night.  Today I tried again, and now it just goes ot the next line in the command prompt. 

Can anyone help me figure this out?  I'm fairly lost but would love to learn!  Thanks for any support you can provide!

---

### Post by dbbolton on 2007-01-04
try installing it from synaptic ?

---

### Post by guyatwork37 on 2007-01-04
Is it under a different name in synaptic?  I tried searching for it, but I got nothing back.

---

### Post by Morningstar on 2007-01-05
I used these two files to set up my wireless card **[ndiswrapper-utils_1.8-0ubuntu2_i386.deb]("http://mirror.xmu.edu.cn/archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb")**  and  **[ndisgtk_0.6-0ubuntu1_all.]("http://mirror.switch.ch/ftp/mirror/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.6-0ubuntu1_all.deb")deb** installed in that order, before copying the windows drivers into a folder in the home directory. I installed both those files direct from a floppy disc which is apparently cheating, but it worked and saved wasting a cd.  

It was my first time using any form of Linux and it went straight through..

I hope the links help.

---

### Post by guyatwork37 on 2007-01-05
Thanks for the help Morningstar!  However, when I opened the first file, it gave me the following error:

"Error: Dependency is not satisfiable: libc6"

Any idea what that means?

---

### Post by Morningstar on 2007-01-05
Sorry, I did my first install of linux about 12 hours ago and I was lucky enough that everything worked first time, my first post detailed how I did it.

But I noticed something when I was researching the files I needed and it may be that it's down to the version of ndiswrapper you've already got loaded, you might have to remove that and use the native version in 6.06.

This is only a guess...

---

### Post by guyatwork37 on 2007-01-05
I guess my problem would then be that I don't know where or if at all the native ndiswrapper is installed.  I can't find it in synaptic unless it is called something else.

---

### Post by Neobuntu on 2007-01-05
One does not normally custom install programs (or compile anything) when almost everything (open GNU) software is available in the best package managment system ever; included upon install of the *ubuntu distribution. This is one of many reasons to use an already done, all works together and popular distribution.

ndiswrapper is already installed but if you can hook up the Internet directly to a wired ethernet port first, use Syanptic (or Adept) to install "ndis-gtk" and you eliminate command line entry with a fancy GUI interface in the "System" menu. "Windows Wireless Drivers" (off the System menu in Kubuntu) is all you click and then point to the XP driver folder and correct *.inf file in it.

Of course, the best thing to do is enter your wireless ssid (on already working, zero driver to setup, devices) and if you can't (bad chip-set company), then spend $20 on a wireless card that will AUTOMATICALLY just work with *ubuntu. Only the crappy poor supported (chip-sets) need baby sitting. NDISwrapper is for stubborn people (like me) who want crap devices to work anyway. That's the truth.

Two chipsets that tend to just work in these things are Zydas and Intel. We're talking about $20 here. Do the math vs. your time.

---

### Post by guyatwork37 on 2007-01-05
Thanks for all of your help!!

I will try this all when I get home.  

The issue here might be that when I tried to connect directly from the DSL router to the laptop, no signal was being picked up, this no connectivity.  Does anyone know what this issue might be?  Thanks again!

---

### Post by macogw on 2007-01-05
> **Neobuntu said:**
> ndiswarpper is already installed but if you can hook up the Internet directly to a wired ethernet port first, use Syanptic (or Adept) to install "ndis-gtk" and you eliminate command line entry with a fancy GUI interface in the "System" menu. "Install Windows Drivers" is all you click and then point to the XP drivers.

When I did that, it told me that the driver was there and that the hardware wasn't (when it was).  I don't really trust the gui (the script saw my hardware). I used [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) to get mine working right.  See if you can find a how-to for your card.  All that is is a script to run ndiswrapper bundled with the Windows driver.  If you have the Windows driver, I think you can use the same script by editing a couple lines in it (changing wherever it says the name of the driver I use to the name of the driver you use).


If your card works and isn't getting a signal, do you maybe have the router set up to whitelist certain computers and yours isn't on the list?  Check for MAC Address filtering.

---

### Post by Neobuntu on 2007-01-13
The GUI just makes it easier for those scared of the (powerful) command line interface. I'm all for time saving ease.

Sometimes one has the wrong XP driver or there are several choices in a set; to try. Also, you may have another driver conflict to remove. I think what it's trying to "say" is, the driver and hardware don't match.  Remember you may have to reboot (or "```
sudo /etc/init.d/networking restart
```").

I even found it important to put the XP driver folder in my home folder and under a short name (easily selected with the GUI "ndis-gtk" package, AKA "Windows Wireless Drivers" then on your app menu).

---

### Post by Neobuntu on 2007-01-13
Things to watch here are often the ndiswrapper needing wifi device may conflict with an automatic kernel module for same device that in development and not working. It's in the way! Thus ndiswrapper will not work until the offending module is blacklisted. All you do is put the name of  the broke module in the blacklist configuration text file.

You may also have to insert ndiswrapper (module) in the right file to load it upon booting.

---

