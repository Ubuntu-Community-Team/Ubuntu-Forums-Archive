---
title: "Will Ubuntu 5.10 Run on my Compaq 1688?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by JEBB on 2005-12-20
I have an old Compaq Presario 1688 LAPTOP.  It has a 400 MHz AMD-K6, 192MB RAM, a 4.8GB HD and an M$ MN520 Wireless Notebook Adapter card. It runs Windows 98 just fine but is glacial with XP Home. If I install Unbuntu 5.10, from the CD, will I end up with a Linux computer sufficiently useful to explore Linux?

Would there be a better version if not Ubuntu?

---

### Post by 23meg on 2005-12-20
Sure, those specs look more than enough. You may want an xubuntu installation (with XFCE desktop environment) if Gnome feels too slow though.

---

### Post by John.Michael.Kane on 2005-12-20
you can always use xubuntu. however what you have there should run gnome just fine..

---

### Post by Mustard on 2005-12-20
You might want to see if you can find your wireless adaptor in this hardware list to see if you need to do anything special to get it working.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by scole on 2005-12-20
Wow will it ever. There should be no problem with that. Except maybe the wireless adapter as said above. I have sucessfully gottem Ubuntu running smoothly on a 333mh PII with 64mb of ram if i can so can you. If it wont boot off the cd your in for some downloading though to get a boot disk that will allow you to boot from cd. But if you need it heres a great link to the boot manager i used. [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm) you would need a raw write program as well use this one [http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm) then dl the binary version. If you want to take a trip into the distro world use this one [www.goosee.com/puppy](www.goosee.com/puppy) it will run and save compleley off the live cd.  It will run top speed on a computer like that. They also have a irc chat channel if you need help.

---

### Post by Dragonbite on 2005-12-21
I hear you mentioning Xubuntu and was wondering, is it an installation like Kubuntu, or do you install bare minimums and then apt-get Xfce4 or how do you go about this in general?

---

### Post by d1337 on 2005-12-21
One method that I am aware of is to install Ubuntu using the server method...as you said, minimal.  Then sudo apt-get install xubuntu-desktop.  From what I've read, this will get everything that you need.  I believe that there is or soon will be an ISO of Xubuntu and I imagine that searching around you'd likley find a way to change your current install to Xubuntu (probably, sudo apt-get remove ubuntu-desktop, then sudo apt-get install xubuntu desktop).  If you search the forums for posts by user Aysiu, I believe that he has done quite a bit of research on how to insure that you toast all the packages that you don't need.  Here's a couple of links

[http://www.ubuntuforums.org/showthread.php?t=96046&highlight=ubuntu-desktop](http://www.ubuntuforums.org/showthread.php?t=96046&highlight=ubuntu-desktop)

[http://www.ubuntuforums.org/showthread.php?t=106372&highlight=ubuntu-desktop](http://www.ubuntuforums.org/showthread.php?t=106372&highlight=ubuntu-desktop)

erm...back up anything that you want before attempting such a task.

d1337

---

### Post by JEBB on 2005-12-21
Thanks for the replies.  It sounds like I've got the necessary hardware.  

A little further reading has revealed that Linux comes in many varieties.  There is only one Windows XP and only one MacOSX, but there are many Linuxes.  My level of computer knowledge is best described as a 'User'.  I know a fair amount about using Windows XP and 98, I teach some courses at a local senior center, and my main computer is a Macintosh (MacOS 10.3.9).

So my next question is:  As a Linux beginner and with my Compaq 1688, is Ubuntu the Linux variety that should be my first choice or is there a better first choice?   Thanks.

---

### Post by d1337 on 2005-12-21
[QUOTE=JEBB]So my next question is:  As a Linux beginner and with my Compaq 1688, is Ubuntu the Linux variety that should be my first choice or is there a better first choice?   Thanks.[/QUOTE]

Oddly, even though these are the Ubuntu forums, most folks I see here will give you their true to life opinion of which distro is best for you.  Maybe take a test
[http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)
I have only run several flavors myself, all of which have been Debian based.  I have chosen Ubuntu and run 5 workstations, 2 laptops and 1 (test)server on Ubuntu.  It has proven to be my favorite while offering quite a bit of "it just works" as well as some challenges that have only taught me/exercised my mind.  Also, these forums are simply great.

Only you can choose which distro is for you.

d1337

---

### Post by deNoobius on 2005-12-21
I come from a similar background (Windows and OSX) and I have to say that after a slightly rocky first few days -- made much easier by asking questions here -- Ubuntu has been absolutely awesome.  Once you learn where things are in the GUI and learn a few basics of the command line, you'll find it's very natural.  My one big problem was getting my laser printer to work, but I got the solution here.

---

### Post by JEBB on 2005-12-21
d1337:  I took the test and it recommended Mandriva for me.  I don't know anything about it yet.

---

### Post by d1337 on 2005-12-21
Honestly, I know nothing about Mandriva either with the exception to what I've read [here]("http://distrowatch.com/index.php?distribution=mandriva&month=all&year=all") at Distrowatch.  It claims to be well geared towards new users as well as experienced users.  I checked out their forums and it appears that there is a helpful user base out there for Madriva/Mandrake.  What I did see, though, is that Mandriva uses rpm for package management.  I have grown very accustomed to apt as I've been using Debian for my production server long before I decided to try Linux on a desktop.  But that's just me.  If rpm didn't work, nobody would be using it.

All I can say is give it a whirl...or give Ubuntu a try.  The decision is yours...which is another bonus of the freedoms of Linux.

d1337

---

### Post by scole on 2005-12-21
Ubuntu will run well but i still say puppy [www.goosee.com/puppy](www.goosee.com/puppy) it works well and will run perfect on a p2 333 with 64 mb of ram. it has great support and a irc room still ubuntu should run fine

---

### Post by Badojo on 2005-12-21
[QUOTE=JEBB]I have an old Compaq Presario 1688 LAPTOP.  It has a 400 MHz AMD-K6, 192MB RAM, a 4.8GB HD and an M$ MN520 Wireless Notebook Adapter card. It runs Windows 98 just fine but is glacial with XP Home. If I install Unbuntu 5.10, from the CD, will I end up with a Linux computer sufficiently useful to explore Linux?

Would there be a better version if not Ubuntu?[/QUOTE]

It will positively work. Graphics how ever can be a problem.

---

