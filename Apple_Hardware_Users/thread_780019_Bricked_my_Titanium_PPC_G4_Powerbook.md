---
title: "Bricked my Titanium PPC G4 Powerbook?"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by Misterbadexample on 2008-05-03
Okay, here goes:

Titanium PPC G4 Powerbook Laptop from 2003. Bought the machine the day before Johnny Cash died, and it's starting to really show that age. It was running 10.2.8 before I tried installing Ubuntu 7.10 for PPC.

First of all, the live CDs would never work. I always got the stock error white screen but recently tried the live video=ofonly option that the new gutsy live CD's have. Still didn't work. So I used the alternate install CD.

Everything in the alternate install worked okay, I had it format and use the whole disk.

On the first startup (and all since) it starts to boot up okay, then moves on to the Ubuntu splash screen. I have some sort of video issue here--apparently there is no proper driver for the video card and it's giving me whatever color the video card can handle.

Anyway, it shows the Ubuntu splash screen for several seconds. There is no animation in the loading bar like on a regular computer.

Then it stops and gives me this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

and then I can enter commands. But being the beginner I am, I have no idea where to go from here. Anyone got any ideas? Even installing another Distro would work for me if my Ubuntu Powerbook is not going to work out.

---

### Post by ssam on 2008-05-03
use ubuntu 8.04 (hardy). it has fixed this bug.

---

### Post by avtolle on 2008-05-03
If you still want to use 7.10 rather than upgrading to 8.04, at the promt type modprobe ide_core; then when the prompt reappears, type exit. This should allow you to continue booting into 7.10. Use the PPC FAQ link in the sticky to see how to make this permanent, so you don't have to do it each time you boot. 

Before upgrading to 8.04, make a copy of your /etc/X11/xorg.conf file, print it out (my recommendation) as you may well need the settings contained therein to edit the same file in 8.04 as I did. 

Good luck.

---

### Post by avtolle on 2008-05-03
Here are two links that may help you.
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ#h...f633929024f1ec]("https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec")

EDIT: Another thought about something that worked for me. I did a dist upgrade from 7.10 to 8.04 on a G4 Cube, rather than a fresh install from CD (which I had done earlier on another Cube). The dist upgrade (from upgrade manager) worked right from the boot, rather than in the case of the fresh install where I had to manually edit my /etc/X11/xorg.conf file to get my screen recognized. So, if you are able to get your 7.10 install up and working, then after fully updating, etc., the dist upgrade might put you right into Hardy without the need to edit the file, as others have had to do.  I hope that makes sense.

---

### Post by Misterbadexample on 2008-05-03
The modprobe ide_core at busybox worked, at least it got me into the OS so I don't feel like I have a big silver brick anymore. I should be able to set it up to boot from the links you gave me, avtolle.

Sound wasn't working, but there was a pretty easy solution on the FAQ I was able to tackle, so it's making noise now. Huzzah!

But the network hasn't worked from the start, and that's a pretty serious problem I can't find a solution for on FAQs, and thread searches gave me nothing... I don't know if it is even finding the devices--neither the Wireless nor the Ethernet connection. It found both during the install and downloaded language packs which baffles me.

I'm downloading Hardy PPC on another machine now but it's going slooooooow. I'll install that as a last ditch effort.

Any solutions to the network trouble?

---

### Post by stream303 on 2008-05-03
Remember that we have now been moved to a ports repository, so doublecheck your /etc/apt/sources.list file.  You may have to manually edit it to point to the correct PPC port repos now at ports.ubuntu.com:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

As far as networking in general - is it a case of no web pages showing up if you try to browse?  Are you behind a router running dhcp?

If so, you may want to put your isp's primary and backup dns server addresses inside the router's setup page, or use the dns servers seen at the bottom right page of [www.opendns.com](www.opendns.com)

We could go on, but let's see if this helps first..

---

### Post by avtolle on 2008-05-03
On the network question: I don't know off the top of my head. Have you tried this from the FAQ? You might need to install this from the CD. Otherwise, perhaps a reboot is in order to see if the problem resolves just from that? 
```
sudo aptitude install bcm43xx-fwcutter
```

---

### Post by avtolle on 2008-05-03
Darn it, forgot to ask, what network card/wireless card you are using. If not an Airport Extreme, the above code won't help by itself, AFAIK.

---

### Post by Misterbadexample on 2008-05-03
@stream303: I"ll keep the ports thing in mind. Thanks.

No web pages show up when I browse, and the network icon in the corner shows me an error. It tells me "no network devices have been found" and gives me the option for "manual configuration." I set up my ethernet to auto dhcp which works fine with all my other machines on the lan.

I may try your suggestion with the router's setup page, but I think some of the hardware isn't being recognized properly and that is where my issue is. I have Hardy running on this Mac I'm using currently and didn't have the first little speed bump with networking.


@avtolle: Pretty sure it's just the stock Airport Wireless not Airport Extreme. As far as ethernet... I don't know. Whatever was standard on these powerbook units in 2003. 

I just ran the code you gave me. It looked like it was downloading something? WTF? I had the install disc in, was it pulling from that? Rebooted and no dice, I guess.

Is there any way to set up a right mouse click, anybody? The trackpad only has one button and the ctrl button and click doesn't bring up the right click menu. I guess I could always use a usb mouse, though.

---

### Post by avtolle on 2008-05-03
Try F12 for right click. That's what seems to work for me.

---

### Post by Misterbadexample on 2008-05-04
It's been a fun and harrowing experience thus far. I just installed Hardy--that automatically fixed the boot problem and also got my network running right again. So that's good news.

The sound is still wonky, but I found that's a very common issue with TiPowerbooks, so there's next to nothing I can do about that.

I'm having a very odd graphical glitch where these black pixels appear in the top menu bar. They're pretty much always there, too. I'll try to look and see if anyone else has that problem, but it's certainly not a showstopper. 

I'm having trouble with getting java/flash/etc to work in my browser. Maybe they aren't going to work on the PPC. I'll look up ways to do that on my own time, but I appreciate all the help you guys have given me.

---

### Post by stream303 on 2008-05-04
I get those little black pixels too with Hardy at the very top line too on my iMac with nvidia card. Like you say, not a showstopper.

The alternative for ppc flash is gnash and other associated utilites, and is being worked on, although I don't really keep up with it.  I think others have got it to a point where it is usable on some sites...

Glad to hear that some of your troubles got resolved!  I actually pulled in two updates since release, so it looks like the new ports.ubuntu.com mods in /etc/apt/sources.list are working..

---

