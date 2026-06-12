---
title: "How do I configure/install drivers for my WCP54G v.3 WiFi card?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by chaofan on 2007-01-31
Ok, so the other day I was tinkering around with some stuff and trying to get my WiFi card enabled, coming to the quick conclusion that I need drivers. I've found a site that contained drivers for every Laptop WiFi card except mine, as well as ran into install problems. (for those who are curious, I did ask the other day, but found alot of problems with my questions, so I am re-instating them with more accuracy)

Here are the things I need help on:
1) How do I get ndiswrapper to function as a command (apparently doesn't even exist)
2) Where can I get a driver for my Linksys WCP54G **VERSION 3** WiFi card (Looked everywhere)
3) Is it possible to use the windows drivers in some way? I installed over my windows due to crashing from OS tweaks.

Potential help questions in the future:
1) How do I get this installed correctly?
2) If yes to 3 above, how do I do it?
3) Will Ubuntu crash my network system if I am behind both a Linksis WRT54G router and a Quest DSL modem with MSN internet?

Also, here are my Laptop specs:
OS: Ubuntu 6.10 (Edgy)
RAM: 256mb DDR laptop RAM (Plan to upgrade)
1.0Ghz to 2.0Ghz adjustable clock P4 Processor (i386 I think)
n-Vidia 420 GO video card


As well as this, I have successfully figured out how to mess with things in Ubuntu due to battling with the drivers and figuring out exactly how sudo and ./Configure worked (freaking capital C, as well as invisible password typing), so I have those bases covered. One thing I do not understand however, is that the drive for storing files (Normally C:\) does not have a single label. The fact that it's missing a label isn't the wierd part, it's how can the driver find specified file locations without first specifying the drive?

---

### Post by muguwmp67 on 2007-01-31
You'll need to install ndiswrapper from the repositories, you'll probably want wlassistant too.

ndiswrapper uses the windows drivers.  Linksys will have them for download on their website.

You can find a how to for ndiswrapper here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrap]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrap")

There's no reason I can think of why ubuntu would crash your network.

I'm not sure exactly what your questions about directories mean.  You might want to pick up a book on Linux, or search for some tutorials on the web  to better understand how things work behind the scenes.

---

### Post by chaofan on 2007-01-31
Ok, well your help got me started in the right direction. I thought that the ethernet would be detected automatically, and when I tried to search for things (like ndiswrapper) it wouldn't update. Now I have ndiswrapper and about 116 updates sitting on my desktop.

The directories question:
Firstly, the last part was just me rambling on. I tend to do that.
Secondly, in Windows, everything is assigned a letter so that the OS knows where to read from and write to. Without these letters, the system shouldn't be able to locate where things are by simply typing /home/username/file. It would have to be C:/home/username/file to tell Ubuntu to look on that specific hard drive. (I used C as an example, because C is the default drive letter in windows).

Once the monster-amount of updates finishes installing, I'll try to set up the WiFi drivers and let you know how it went.

---

### Post by muguwmp67 on 2007-01-31
The linux file system is similar to windows, but not the same.  I'm a linux noob too, so my explanation may not be technically accurate.

In windows,  *partitions* get their drive letters.  That's where the C: D:, etc come from.  You can put two partitions on a single hard drive and they will appear as two different letters.  

(I recommend to my students that they do this on new windows systems to keep programs and windows on one partition and move the data to the other, it makes reinstalling windows much easier when the time inevitably comes)

So in windows you have c: and d: for your partitions.  In linux partitions all get mounted into the root file system (this is the top level), everything gets mounted under this.  So, if you mount a new partition in linux (find a faq in the wiki on this if necessary) It will appear as an entry under the root ('/'). 

Example:
I have a hard drive system for my media files.  In windows, this drive is mounted as F:/.  
While mounting it in linux, I gave it a name called /winmedia.

It then mounts as  /winmedia in the linux file system.  

Its actually nicer this way because you don't have to worry about things like drive letters changing.

Hope that helps some.

---

