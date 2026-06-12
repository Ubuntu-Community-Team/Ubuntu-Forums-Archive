---
title: "Just installed Xubuntu. Fonts are so small I can't read anything."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by jmccrac on 2007-12-01
I just installed Xubuntu on a PC I have hooked up to a 720p HDTV and all the fonts appear as small irregularly shaped dots. I clicked the Firefox icon and it came up with a screen full of these irregular shaped dots. However, if I hit ctrl + a bunch of times the text in Firefox alone becomes readable.

So, it looks like the system fonts are all set to be far too small to read. I'm not the least bit familiar with Xubuntu or Ubuntu so I have no idea how to fix this by memory. Also, I'm completely new at Linux in general so if anyone has any solution I might need step by step instructions in order to attempt a fix. By that I mean, "Click here, scroll down and click the 4th thing from the top." Remember, I can't read any of the text in the menus.

Thanks in advance.

---

### Post by overdrank on 2007-12-01
> **jmccrac said:**
> I just installed Xubuntu on a PC I have hooked up to a 720p HDTV and all the fonts appear as small irregularly shaped dots. I clicked the Firefox icon and it came up with a screen full of these irregular shaped dots. However, if I hit ctrl + a bunch of times the text in Firefox alone becomes readable.

So, it looks like the system fonts are all set to be far too small to read. I'm not the least bit familiar with Xubuntu or Ubuntu so I have no idea how to fix this by memory. Also, I'm completely new at Linux in general so if anyone has any solution I might need step by step instructions in order to attempt a fix. By that I mean, "Click here, scroll down and click the 4th thing from the top." Remember, I can't read any of the text in the menus.

Thanks in advance.
Hi and welcome, I would suggest using a crt or lcd monitor until you are familiar with Linux, this link may help some 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by jmccrac on 2007-12-01
> **overdrank said:**
> Hi and welcome, I would suggest using a crt or lcd monitor until you are familiar with Linux, this link may help some 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I was afraid you would say that. Unfortunately, my only other machine is an iMac with a built in screen. Basically, I don't have access to another monitor.

I would like to clarify that the fonts aren't just "hard to read" small. They're "like 3 pixels high" small. Everything else looks perfectly normal and legible. This includes any words that are just images and not live text.

---

### Post by overdrank on 2007-12-01
> **jmccrac said:**
> I was afraid you would say that. Unfortunately, my only other machine is an iMac with a built in screen. Basically, I don't have access to another monitor.

I would like to clarify that the fonts aren't just "hard to read" small. They're "like 3 pixels high" small. Everything else looks perfectly normal and legible. This includes any words that are just images and not live text.

Ok then I would ask why you chose xubuntu, xubuntu is usually used with low memory systems and if that is not what your system is, then why not try Ubuntu. and if you want xfce then you may want to add it to the system after you have a up and running system.

---

### Post by jmccrac on 2007-12-01
> **overdrank said:**
> Ok then I would ask why you chose xubuntu, xubuntu is usually used with low memory systems and if that is not what your system is, then why not try Ubuntu. and if you want xfce then you may want to add it to the system after you have a up and running system.

That's a fair question. Basically, it's a low spec system. 128mb RAM with a 1.6ghz processor. I think the original OS was Windows ME if that tells you anything. I figured it would be nice to browse the internet from my couch among other things.

But at this point I take it this isn't a common glitch? I was hoping it would be the sort of problem where someone would say, "Oh, this happens all the time! Press XYZ and you're set."

---

### Post by overdrank on 2007-12-01
> **jmccrac said:**
> That's a fair question. Basically, it's a low spec system. 128mb RAM with a 1.6ghz processor. I think the original OS was Windows ME if that tells you anything. I figured it would be nice to browse the internet from my couch among other things.

But at this point I take it this isn't a common glitch? I was hoping it would be the sort of problem where someone would say, "Oh, this happens all the time! Press XYZ and your set."

Ok then with a 128mb system you made the right choice. Excuse me for asking but I am trying to narrow things down. Have you tried to reconfigure the xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Use that command in the terminal located under applications, accessories. If you can not see to enter that command then you can try from recovery mode. It is the second choice from the grub boot ( usually ) then enter that command and the reboot with this command ```
reboot
```

---

### Post by jmccrac on 2007-12-01
> **overdrank said:**
> Ok then with a 128mb system you made the right choice. Excuse me for asking but I am trying to narrow things down. Have you tried to reconfigure the xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Use that command in the terminal located under applications, accessories. If you can not see to enter that command then you can try from recovery mode. It is the second choice from the grub boot ( usually ) then enter that command and the reboot with this command ```
reboot
```

I tried that command from recovery mode but there was no improvement after rebooting. To be honest, this project has exhausted my patience for tonight. But I do appreciate your help all the same.

Thanks!

---

### Post by louieb on 2007-12-01
Don't know much about xfce. But if  its like Fluxbox. Font size can be controlled by a theme. I've resized my fonts in Gnome and Fluxbox. 
May want to head on over to the how to section and do a search on themes. Good Luck. BTW I think you would like Fluxbox on that PC.

---

### Post by alphaniner on 2007-12-02
Sorry to butt in here, but I'm in a similar pickle.  I'm brand new to Xubuntu (7.10) and the fonts are killing me.  I'm using a 21" CRT at 1152X864.  I've fiddled with the font type and size in the User Interface Settings, but that affects both the smaller text (such as on the Panels and in the File Manager) and the larger text (such as in the User Interface Settings window).  So in order to get the smaller text to a legible size, I have to make the larger text *too* large :(  Is there a way to modify them independently?

And then there's Firefox.  I have to Increase the text size once or twice on most pages, but on my Windows box with the same monitor at the same resolution the default size is usually spot-on, not to mention so much more 'crisp'.  Even when I increase the fonts to a larger size than I would in Windows, I still seem to experience more 'eye fatigue.'

The main reason I chose Xubuntu is because the company I just started working for uses it, and I wanted to get some more experience with it.  Aside from this font issue I'm loving it so far, and I can now see it becoming my primary OS.  I've thought about switching to Ubuntu, but I'm not sure if I have the specs.  I've got a 1.2 GHz P3 and 512M RAM, would that cut it?

---

### Post by rjcope728 on 2007-12-12
I too am suffering from 3 ailments -
1)the fonts are so small I can't read them.
2)all the scripts I have tried don't work.
3)since this is the 3rd time in a year of trying to get Linux to work, on anything, my patience is wearing mighty thin!

Although I hate almost everything about Microsoft, I can load up XP on all the machines in my house in about an hour apeice. 

I have completely built a machine totally dedicated to Ubuntu, no MS junk ever on it, but I've had it for tonight, can't see anymore, F&*&ing blind now! 15 hours in 1 day is enough, boo for linux tonight.
 I thought with all these geniuses out there, someone could write an OS that doesn't require so much scripting, just load the thing up, like windoze!!  Glad I kept my hacked copy of Corp. Edition of XP.

enough complaining, just frustrated and my area is in the middle of a bad ice storm, trees falling everywhere.:confused:

---

### Post by rjcope728 on 2007-12-12
Much better today, bought 21" monitor and life is good in the Linux world. Bigger more modern Dell monitor was just the ticket, only $20 US. Fonts are big enough to read and the rest of the graphics seem much better at 75 Hz. and the default 1024 X 768 resolution.

---

### Post by oldcity on 2007-12-12
While I know you wanted to change the font size at boot.
You can use ctrl + to increase the font and ctrl - to decrease.
hth
oldcity

---

### Post by danwood76 on 2008-01-15
I just had a play with xubuntu and was getting the same problem you were having.

When you reconfigure the xorg.conf I noticed that the files section was empty, thus missing the font dpi infos.
Deleting this section fixed it and after a restart everything was nice and readable again.

hope it helps,
Danny

---

### Post by footfall on 2008-02-15
> **danwood76 said:**
> I just had a play with xubuntu and was getting the same problem you were having.

When you reconfigure the xorg.conf I noticed that the files section was empty, thus missing the font dpi infos.
Deleting this section fixed it and after a restart everything was nice and readable again.

hope it helps,
Danny

Thnx a LOT!, the only thing that worked.

---

