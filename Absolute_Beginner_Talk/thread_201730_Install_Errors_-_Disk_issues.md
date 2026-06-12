---
title: "Install Errors - Disk issues?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Grunth0s on 2006-06-22
Hi,

First time trying Linux, and know absolutely nothing about it, so apologies if I sound a little dense.

I have an old IBM laptop (PIII 700, 256meg) that I want to put Ubuntu on, to get a feel for Linux, and to use on a daily basis.

When I try to install, it will just hang on a completely black screen, with no further input accepted.

I can run 'Live' linux on it (Knoppix, Meppis, etc), and the laptop will take a Windows XP install without any problems.

I think that there may be an issue with some damaged sectors on the hard drive, and I didn't know if this could cause Ubuntu (and a couple of other distro's I have tried) to fail to initialise the disk properly, and therefore fail?

Any suggestions would be appreciated.

---

### Post by hotbrainz on 2006-06-22
Have you tried the Live version of Ubuntu?

Did it run fine..

---

### Post by Grunth0s on 2006-06-22
I have been running Slax (live) on it for the last few days.

A friend recommended Ubuntu, and I would like to try it, but haven't yet tried the live version (only downloaded late last night, and stuck at work at the moment).

I have tried a few full distro's for installation, and all are experiencing the same problem.

I am assuming that 'live' Ubuntu will work as the Slax and Meppis ones did, and the full version will fail at the install, but I will be testing this properly tonight.

I still believe that disk errors are causing the problem, but wonder if there is anything I can do to remedy this from a 'live' boot.

---

### Post by hotbrainz on 2006-06-22
I have tried a few other linux distros myself, but Ubuntu was the first which had 90% of my hardware running right away. So it must run on your system (hopefully).I tried Live version first though. Doesnt  the CD You download have an option for a LIVE session ?

If yes, then go for it. See if the Live session works. IF not we will take it from there :) Good luck

My guess is that your download Cd is corrupted. This happens all the time. So please try LIVE and tell us what u got!

---

### Post by Grunth0s on 2006-06-22
I will be installing this evening, so hopefully, all will be well.

Does the standard 6.06 Desktop version have the live option? If it does, that would help.

Really would like to get into Ubuntu, like I said, I have looked at other distro's, but after having Ubuntu recommended to me, and looking around these forums (which look to be awesome), it looks like this is the place to get started!

---

### Post by hotbrainz on 2006-06-22
the 6.06 version happens to be the latest version and is called the Dapper drake. Ya it does have a Live version. Just try it. It should work.

---

### Post by Grunth0s on 2006-06-22
Thanks for the information so far :)

I am sure I am going to have many more questions before my Linux experience is sufficient to use it properly.

---

### Post by pellgarlic on 2006-06-22
wait a sec - what version of ubuntu have you been trying? if you downloaded the newest version - 6.06 ("dapper drake"), then you already have the "live" cd - it is one and the same as the "desktop install" cd. what you could do is try downloading the "alternate" cd, which offers a text-based installation procedure, rather than a gui one, as it seems like it is a graphics problem you are having.

at what point do you get the black screen? do you get to see anything at all?

---

### Post by Grunth0s on 2006-06-22
I haven't yet tried the Ubuntu CD, as I said, I have tried other distro's and 'live' CD's, but have decided to go with Ubuntu, which I downloaded last night.

Other distro's don't seem to want to fire up at all, the CD boots, presents a menu which I select install from, and then they go away for a few seconds before the system hangs. I am assuming at that point, that they are trying to initialise the disk (or is it mount the disk in Linux?) which is why I think that the disk errors could be the cause.

As Slax works on the laptop with no problems ('live' version), I don't think it is a graphical problem, as it would exhibit the same problems?

I will be going for the Ubuntu 'live' test later on today, and then try for the full install, assuming the live version works.

---

### Post by pellgarlic on 2006-06-22
ah, i see. i misunderstood your original post. thought you were having problems while trying to install ubuntu. 

seems strange that "live" cds work, but "install" cds dont... what distros have you tried to install?

---

### Post by Grunth0s on 2006-06-22
Suse, an old RedHat distro, and Knoppix. Meppis 'live' works fine, but full installs don't which is why I suspect the disk.

One other thing that may not be helping is my DVD drive doesn't like my burnt DVD's, although seems happy enough with CD's. Suse was on a DVD (which is a probably cause). My DVD of Vista Beta 2 also failed, but that was with a specific file corruption message, which I don't get with the Linux installs.

---

### Post by underdog on 2006-06-22
Vista Beta....pffft. I've heard about 2% of the people that attempted to get it to work actually get it working. 

As far as display problems, just check out the boot options, setting a vga=??? option might help. 

If no installs work, it could be a bad HDD, or you may just not have your partitions set up right. What is happening when you try to install those distros?

If you do get 'stuck' using a live cd, you can still do a lot with it. You can save pretty much everything you do to your HDD (or the internet in some cases). Even if your HDD is crapped up, you can probably still find somewhere to put a partition to save changes made with a LiveCD

---

### Post by pellgarlic on 2006-06-22
with the ubuntu "dapper drake" cd, as i said earlier, the "live" and "install" cd's are one and the same - so if the "live" cd boots ok, double-click on the "install to hard drive" icon that you see on the desktop. hopefully that should get you going :)

if not, and you suspect hard drive problems, it might be worthwhile downloading "ultimate boot cd": [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) (it's free)

it has many really useful utilities on it, including various hard disk diagnostic programs, allowing you to check for bad sectors, etc. there is a "lite" version , and a "full" version - which includes the equally useful "insert" linux-based recovery environment.

---

### Post by Grunth0s on 2006-06-22
Don't really want to stay with the 'live' stuff, as it stops me doing the interesting things, like installing applications and stuff. Vista I have installed on a different machine now, and is working fine (once I sorted some driver issues out).

I don't think there is a great deal wrong with the hard drive, other than some dodgy sectors, just didn't know if this would be enough to stop Linux installing? I don't actually get to a point in the installation where it will allow me to specify the partitions.

---

### Post by underdog on 2006-06-22
What actually happens when the install fails?

---

### Post by Grunth0s on 2006-06-22
[QUOTE=underdog]What actually happens when the install fails?[/QUOTE]

Nothing....

Select install option, text mode Linux fires up, screen goes blank....

Screen stays blank....

Computer hung

---

### Post by pellgarlic on 2006-06-22
what's the last text you see before the screen goes blank? if you can catch the very last line (as long as the text isn't moving too fast) that could be a big help...

---

### Post by underdog on 2006-06-22
Try using 
```

linux vga=771 nolapic noapic

```
when booting

---

### Post by Grunth0s on 2006-06-22
Think I have found part of the problem.

It would not boot to the 'live' version while I had my PCMCIA Wireless Card physically installed in the laptop. For some reason, it would hang immediately after the 'starting gnome' text appeared on the screen. Not sure why this would be, the Slax live CD had no problems with this card, and installed the drivers for it automatically.

Without the card, it boots into Gnome happily, although the PS2 mouse no longer works, the keyboard 'nipple' mouse is functional.

At this time, I would hazard a guess that the default install has some issues with IBM laptop devices, specifically the PCMCIA bus and the PS ports, which could explain some of my previous issues.

I will get the full install done, and see what happens.

Thanks for all your help so far

---

### Post by pellgarlic on 2006-06-23
just for the record, and for your future reference, you can also use "nopcmcia" as a boot option. might be useful, rather than having to physically remove the card.

---

### Post by Grunth0s on 2006-06-23
Thanks for that.

Going to have a look round for some appropriate IBM Laptop drivers as well, and see if that is where the problem is.

Just to let you know, the install went pretty well, and Ubuntu is now loaded, just got to get the other bits sorted, for things like MP3 and DVD playback (have found plenty of resources for that). Then I can start having a play with installing some apps.

---

### Post by pellgarlic on 2006-06-23
hooray! welcome to ubuntu :)

---

