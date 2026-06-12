---
title: "Install Issues: Partitioning..."
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by toiletdude on 2007-07-12
Hey guys.
I'm installing Ubuntu 7.04 from a burned LiveCD.

Now, here's my issue...

Whenever I install Ubuntu from the disk, it works fine until step 4 of 7... (partitioning)

I set the partition, click Forward, and it doesn't work......
It gives me an 'Operation Failed' error... I dont understand why...

I'm trying to partition a 20 GB HD (13 GB to windows, 7 to Ubuntu). 
On the slider, I select around 13.3 GB. (But for what?? Windows I assume.)

Any reasons I could be getting these errors?


Thanks... I'm hoping to get this installed tonight.:)

---

### Post by ftpaddict on 2007-07-12
It gives me an 'Operation Failed' error... I dont understand why... < **Maybe the live CD had a corrupted file.**

"I'm trying to partition a 20 GB HD (13 GB to windows, 7 to Ubuntu). " <** The minimum I could get was 20 GB for Ubuntu alone. It did not want to shrink less than that.**

If the rest of your system "matches" the capabilities of your hard disk, perhaps it would be better to try xubuntu instead. [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Hendrixski on 2007-07-12
You may also want to try the Alternate install CD... it doesn't have the nice graphical interface, but it has worked for me when the regular CD hasn't EVERY TIME.  and I've installed a lot of Ubuntu.  All of my friends and family are on it now.

You can DL that on the website as well.

---

### Post by Hendrixski on 2007-07-12
oh... and by the way

WELCOME TO THE COMMUNITY!
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others. 

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by toiletdude on 2007-07-12
Thanks, I think i will try Xubuntu... I'll definately keep my Ubuntu CD handy, though.
(Xubuntu looks a lot lighter on sys requirements)

And thanks Hendrixski. :)

---

### Post by TheTaylorEffect on 2007-07-12
I ran into a similar problem with an older "legacy" system yesterday afternoon. with an old system you might want to try installing it with smaller steps.

I managed to get XUbuntu  onto a Pentium II laptop with 128mb of ram by installing [Ubuntu Server Edition ]("http://www.ubuntu.com/getubuntu/downloading?release=server-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=")on a 4gb partition, connecting to the internet, and using the 

```
 sudo apt-get install xubuntu-desktop 
```

command from the server console to add the Xubuntu desktop. 

You could also use:

```
sudo apt-get install ubuntu-desktop
```

for the Gnome desktop (if you think your system is robust enough to handle it).

---

### Post by toiletdude on 2007-07-12
I think i'll go with Xubuntu for now, and if anything, run that Xubuntu install command from a LiveCD...
would that work? running that Xubuntu install command from a LiveCD of Ubuntu?

---

### Post by TheTaylorEffect on 2007-07-12
> **toiletdude said:**
> I think i'll go with Xubuntu for now, and if anything, run that Xubuntu install command from a LiveCD...
would that work? running that Xubuntu install command from a LiveCD of Ubuntu?

I might be mistaken (I'm something of an Ubuntu rookie myself) but I think in order to install the ubuntu-desktop or xubuntu-desktop packages you have to have the server installed. Those specific packages are just graphical interfaces for the server (with some extra useful software assembled in a single neat package by Ubuntu).

Are you trying to preserve an existing install of Windows, and create a dual boot system?

And what are the specs of your system?

---

### Post by toiletdude on 2007-07-12
I'm trying to preserve an existing install of Win XP until I can get the OS working...

Specs:
900 Mhz Processor (P3)
512 MB RAM
20 GB HD (10 GB open)
8 MB Video Card
Crystal SoundFusion Soundcard

And from what i've read, you don't need the server to use the desktop, but could anyone confirm/disprove this? I need the download running by tonight... Going on a trip tomorrow and am gonna takr my laptop if i can get a Xubuntu copy working.

---

### Post by GMachine_24 on 2007-07-12
Ok..........here is the most likely source of your problem(s):

1. Bad hardware (not likely if you've used it before and it ran fine).

2. Bad OS install disk. Try burning a new disk at a slower burn rate - like 4x maximum. Use new media; and if you have to try a different burner and burning program. I've had issues with all of these in the past.

Slow burning a new disk, however, has been the solution more than anything else.

And . . . I don't think you need server files installed to install or use the 'live' version of Ubuntu (or Knoppix, etc.). But since I'm a little confused about where/how/why someone would install/need the server software (as mentioned in previous post) I can't offer more suggestions.

Remember: all else being equal, the simplest solution is usually the correct one.

Welcome to Linux.

--gm

---

### Post by TheTaylorEffect on 2007-07-12
Dual boots can be tricky on older machines.

a poorly configured, or improperly ordered partition might be generating that error.

I'd stick with Xubuntu with those specs... but if you're able to run LiveCDs you might want to give this article a read: 

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

It helped me immensely during one of my first dual boot configurations. It suggests using the[ Linux System Rescue Live CD]("http://www.sysresccd.org/Main_Page") to partition the drive. And that has worked really well for me.

The Linux System Rescue CD is a bootable CD with a bunch of VERY handy tools on it. 

After that, I still suggest you install the Ubuntu server edition then add the desktop with the "apt-get install" command I mentioned before (but that is up to you).

---

### Post by toiletdude on 2007-07-12
alright, thanks GM. 

I'm still downloading Xubuntu, but i think i'll burn a new Ubuntu LiveCD as well and try it.
Now I'll have something to do on an 8 hour car ride to Mossouri...:D

EDIT: @ TTE:  I've seen that site before, looked at it a bit when i was plotting my possible migration.

---

### Post by TheTaylorEffect on 2007-07-12
> **toiletdude said:**
> 
And from what i've read, you don't need the server to use the desktop, but could anyone confirm/disprove this? I need the download running by tonight... Going on a trip tomorrow and am gonna takr my laptop if i can get a Xubuntu copy working.

Don't let the term or title "Server Edition" scare you. It's simply the Ubuntu operating system without a graphical interface (which you would add with the command I mentioned before).

When you install any version of Ubuntu, you are installing the server, an X interface (like Gnome, or XFce) and some other pre-configured software.

Installing the server first and adding the desktop second is less resource intensive then running the install off the live CD. The "server" is just the underlying operating system.

To draw a Microsoft friendly analogy: the "server" is to the ubuntu-desktop what DOS was to the older Windows operating systems.

Greenmachine is correct in saying you don't need the server to run the live CD... but if you *install* Ubuntu in any form, you are installing the "server". And I think doing it in small steps with older hardware is the way to go.

But, definitly try making a new CD at a slower speed... I can't tell you many times simple problems (like loose cables or defective media) have caused me days worth of stress!

---

### Post by toiletdude on 2007-07-12
alright, thanks everybody.

:) I have Xubuntu downloading, and my copy of Ubuntu ready to be burned (prolly... 2x for each). I may look into the server edition, but seeing as I won't have internet access, I'll try this first. And wait for the server edition download when I come back (if this fails).
After some brief reading on Xubuntu, it seems the way to go as it's much less intensive (about half) than Ubuntu. 

Hopefully these things will work, if not, server edition and small steps. 
:D Once again, thanks everyone. Linux... Here I come!

(BTW, I really like the way Ubuntu/xubuntu look/work. Another selling point in my migration... My brother things I'm crazy for liking Linux... ([x]ubuntu mainly :) )

---

