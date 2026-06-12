---
title: "Nvidia 6800 Driver for G5 Tower or Bust!"
date: 2008-03-25
forum: Apple PPC Users
---

### Post by barakuda on 2008-03-25
Word on the street is it's not so hard to cobble together a custom video driver. Well, I have the time. And I have at least enough skill to learn the skills I'll need purty quick like. So let's do this thing. I have a Dual 2 GHz G5 Tower with an Nvidia Geforce 6800 in my one and only AGP slot. I have two displays. I'll spare you the details, 'cause at this point I figure they're still more or less irrelevant. What do I need to read, and what's the hardest part? If any of you wizards (you know who you are) could recommend a book or two and throw out a caveat or two, I'd be much obliged. And I'll share, of course.

Ubuntucats, hoooooo!

---

### Post by slacka-vt on 2008-03-25
This ought to get you going

[http://ubuntuforums.org/showthread.php?t=189752](http://ubuntuforums.org/showthread.php?t=189752)

I have a PowerMac Dual 2.7 G5 but I have an ATI 9600 graphics card
so I can't hep you with that part.

I used the net-install Hardy 20080314 "Mini.iso" Net-Install
on both the fore-mentioned system and a PowerBook Ti 900 Mhz with  768 RAM.

Just as a test, The Hardy Live-Cd works flawlessly on my PowerMac also (even for installation)

Both of these installed with NO problems and very little manual configuration.
The PowerBook's WiFi-b card was immediately detected with the Net-Installer and I was able to complete the entire installation process wirelessy (from my couch while watching American Idle jk)

I am a total Linux newbie.

There are so many people having problems with similar systems ( i.e iBook G4, Mac Mini G4's and iMac's ) I just can't believe the amount of issues people are having. I'm trying to help in the forums but it's just overwhelming.

One major thing I have noticed is that:

ISO IMAGES MUST BE BURNED AT 8X OR LESS . . .
they will boot if they are burned at maximum speed but you will, I REPEAT,
you will have issues installing.

This goes for all Installation cd's / dvd's.
Just because the CD boots, doesn't mean it's going to install properly.


Another thing, There have been instances when I have booted my computer PowerBook,
I get through the Yaboot loader then there's no graphics, just a cursor (not even a terminal).
Sometimes this will happen after booting several (3-4) times, and then the 5th (or 6th) time. . 
voila .. it just magically works.
I don't ask why.

On my PowerMac G5, Ubuntu works EVERYTIME

~s

---

### Post by ssam on 2008-03-26
> **barakuda said:**
> Word on the street is it's not so hard to cobble together a custom video driver. 

:-) i think it is a bit trickier than that, but people do it.

the nouveau [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) project are writing a new opensource drive for nvidia cards. in the past year they have made good progress in 2d, and are starting do to some 3d stuff.

have a read through their site. especially the irregular Nouveau Development Companion, [http://nouveau.freedesktop.org/wiki/IrcChatLogs#T2008](http://nouveau.freedesktop.org/wiki/IrcChatLogs#T2008)

i think they are especially interested in testers and developers on powerpc.

---

### Post by barakuda on 2008-04-01
:guitar:

Hells yes. I'm'a read up on everything yall posted, and'll update in a little bit. Stay tuned.

---

### Post by barakuda on 2008-04-01
> This ought to get you going
[http://ubuntuforums.org/showthread.php?t=189752](http://ubuntuforums.org/showthread.php?t=189752)

I checked that out, but it's mostly about a x server config and multi-monitor problems on Dell machines. I didn't see anything about building video drivers or any kind of Apple machine.

> I have a PowerMac Dual 2.7 G5 but I have an ATI 9600 graphics card
so I can't hep you with that part.

I hope you clean your 9600's fan out semi-regularly. Mine melted like a 'foo. Hence the Nv 6800, hence the question.

> On my PowerMac G5, Ubuntu works EVERYTIME

I guess I should make it clear that the problem I'm having *isn't an unexpected one*. Nvidia doesn't make PPC linux drivers, and I haven't seen anything to indicate that they will. This isn't a problem with my install, it's a problem with the world.

The thearch continuth.

---

### Post by 3rdalbum on 2008-04-02
Writing a video driver that can get some basic video output going? Easy enough. Writing one that can give you any sort of acceleration? Very difficult.

---

### Post by barakuda on 2008-04-03
Yes, one of my friends just told me that would mean writing it in c++ if I was suX0rz, and in assembly if I wanted it nice. Two words, rhymes with "Duck hat." Checking out newworld now...

---

