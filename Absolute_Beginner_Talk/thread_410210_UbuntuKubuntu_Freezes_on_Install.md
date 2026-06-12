---
title: "Ubuntu/Kubuntu Freezes on Install"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by wiseguyxp on 2007-04-15
Hey, I'm pretty new to Linux and decided to give Ubuntu a shot, so I got a copy of Kubuntu 6.10 and tried to install it on an old EMachines that I have.  I'm trying to make the machine into an SQL Server, FTP server, and a few other servers, so it's going to basically be my very weak version of a server, but I want it also to be easy to use as far as just Internet use and music for the rest of the family.  I have 2 hard drives in the machine.  One is 20 gb and has 15gb windows xp pro partition and a 5gb Linspire partition.  The other hard drive is an 80gb which is completely blank.  I want to put maybe a 20gb Ubuntu/Kubuntu partition on there and leave the rest for network storage space.  I'd like to know which version of Ubuntu I should use first.

Anyway, with the 6.10 Kubuntu I've been trying to install, I boot from the CD and select "Start/Install" from the options that come up.  After this, it goes to the little loading screen for Kubuntu and eventually the little loading bar freezes after about a minute or so (I've left it running for hours and it still did nothing).  I'm sure it's not a problem with the CD, since I loaded it up just fine on my other machine.  I've also tried Ubuntu 6.10 (which does the same thing), Kubuntu 6.06 which, at the loading screen, says "Loading Essential Drivers... Ok", but freezes at "Mounting root file system".  I've also tried Ubuntu Server 6.06, which freezes after it detects the devices.  So second, I'd also like to know how to get around this dilemma.  Any help would be appreciated.

By the way, the EMachines is 766mhz Intel Celeron with 256mb RAM.

Thanks,
Wiseguyxp

---

### Post by Seisen on 2007-04-15
It could a problem with the cd-rom or you computer since it is kinda old. If you trust trying to make it into a server than all you need is a server install cd. If you want the gui it doesnt' matter which one you use, it just depends on your preference of whether you like Gnome or KDE.

---

### Post by aberry5555 on 2007-04-15
You may need more ram to do the install, either try using the text-install download or try finding another stick of ram (if you have one laying around). 

This is only a guess, however, so don't take my word for it, but if it's freezing trying to make the root file system it might be running out of memory.

---

### Post by wiseguyxp on 2007-04-15
I'd think that it'd tell me if it were to run out of RAM during the install, but I'm not really sure since this is my first Ubuntu install, and the system requirements say that 256 is the minimum

---

### Post by juantovarm on 2007-04-15
Have you tried the server edition? I think that might be just what you need

---

### Post by wiseguyxp on 2007-04-15
Yeah, I'm gonna try to install Ubuntu Server 6.10.  I'm downloading it right now, but I probably won't get to actually installing it tonight.  Hopefully it will decide to just magically work...

---

### Post by aberry5555 on 2007-04-16
it probably wouldn't tell you if you ran out of memory as, unlike windows, it doesn't have a dynamic page-file system, you have to set one up yourself after install if you need it (also if you're running 256meg and you do happen to be able to install it you might want to set up a "swap" partition, which is the same as a page file in windows.)

---

### Post by wiseguyxp on 2007-04-16
Yeah, I'll definitely set up a swap (probably fairly large).  I thought that XP Pro would probably use up more RAM than most, if not all, Linux distros.

---

### Post by Terl on 2007-04-16
I had the same pc a while back.  I did have Debian running on it as well as Fedora and slackware.  I also had a video card (it originally was a shared ram card as it had onboard video--if yours does too it cuts into that 256 pretty good).  You can regain the ram by adding a cheap video card and disabling the onboard video via the bios.

The pc lagged a but with kde so you will want to stay with lighter weight desktops.  And, yes, bigger swap file helps.  It will not be a speed demon by any stretch but it will work.

---

### Post by wiseguyxp on 2007-04-16
Oh yeah, I didn't think about the onboard video cutting into the RAM.  Hopefully I can get some more RAM soon, or maybe use a smaller distro.

---

### Post by Terl on 2007-04-16
If you cannot get more ram (or even a cheap nvidia card) give Zenwalk Linux a try.  It worked really well on my eMachine.

---

### Post by wiseguyxp on 2007-04-17
Well, I finally got Ubuntu Server 6.10 burned to a disk and tried to install it.  Almost needless to say, it didn't work either, but it at least gave me some error messages to go by.  It said something like "[some numbers] Buffer I/O error on device hda, logical block [some more numbers]" like 6 times, then "Invalid" something that I can't make out because it goes too fast.  It keeps going after that, though until after I choose the language, keyboard, and it detects the installed devices, then it goes to a blue screen with a gray bar at the bottom and freezes.  This makes me think it's a drive error instead of a RAM issue.  If I can't get it to work, would I be able to just put the server's hard drive into my computer and install it like that?

---

### Post by FeelTherush1 on 2007-04-17
you should try a quiet splash boot. when you start the live cd, press F6 and then delete the part that says "quiet splash" you will get more info from this. btw.... u dont happen to have an ATI video card do you? i get the same thing with my ATI X800 GTO (AGP). I also am looking for a solution for this problem.

---

### Post by wiseguyxp on 2007-04-19
Tried it and it basically spammed me about the I/O error still

---

