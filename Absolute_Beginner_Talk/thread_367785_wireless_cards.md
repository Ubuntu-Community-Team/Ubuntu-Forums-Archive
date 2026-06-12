---
title: "wireless cards"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-02-22
I found out a cheap zonet usb wireless works with ndiswrapper!!

i found this and im posting it because there are way too many people asking about wireless cards.


[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Hope it hepls!

However i dont know what to do to make it work 
:confused: 

but at least there is hope....

---

### Post by gigaferz on 2007-03-18
It works   zonet usb zew2502

The steps sound easy but its kinda confusing
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

The unistallation part was the hardest .
since I did not understand where the ndiswrapper directory was, I had to do it manualy.

Open a Nautilus or knoqueror from the terminal..  sudo nautilus

Now in other terminal type locate ndiswrapper

and delete each file in that list.

Now the rest is piece of cake.

If your device is present in System _> adminstration->networking

Its done you are just one step away from wireless..!!!

I think the FIRST advise to all the persons with wireless problems is to unistall the default ndiswrapper.

I forgot to mention I am using Ubuntu Ultimate Gamers Edition

I believe it includes many files needed for compilation or something like that. Hope it helps

---

### Post by gigaferz on 2007-03-28
Hello!

I installed another Gamers Edition, on my main PC.

And I also have a zonet product , but this is a pci wireless.

Since I did not like the method above I decided to try something else before doing it.

I got this before updating
 sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


After a few hours of research, I just updated to ndiswrapper-utils-1.8 from the repositories.

I went to the directory where I have the inf file, after that I installed the driver

Once the driver was present and hardware present, I did the modprobe, then i did a scan and it was working, later it appeared on the networking screen.

I know I do not have detailed instructions, but feel free to contact me if you ever read this and need some help, 

This is getting better!!!

soon wireless problems will become just another memory.

---

### Post by Sawert on 2007-06-09
Works great for me! I have an Zonet 2502 and at first I found it hard to get it to work. Quite soon though, I found ndisgtk when i did an apt-cache search.

After installing ndisgtk (apt-get install ndisgtk) and ran it as root, I just had to pick the inf-file from the XP driver and suddenly my wireless USB-adapter worked out great! I can now see all wireless connections that's avalible and it's easey to see what signal I have and to connect!

Thanks for the tip about ndiswrapper, just made it easier when there was a GUI for it all!

---

### Post by gigaferz on 2007-06-22
im glad to hear this post helped somebody

---

