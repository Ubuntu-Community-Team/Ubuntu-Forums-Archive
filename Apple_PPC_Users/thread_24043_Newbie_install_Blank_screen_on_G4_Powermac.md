---
title: "Newbie install: Blank screen on G4 Powermac"
date: 2005-04-05
forum: Apple PPC Users
---

### Post by Tofu on 2005-04-05
I'm a newbie to Linux, and his is my machine...

[IMG]http://www.cupertino.de/data/models/g4.gif[/IMG] 

It's a 1999 vintage 350MHz Sawtooth G4 (AGP), with the dreaded ATI 128 Pro graphics card that came standard with the machine. It's connected to an LG Flatron L172WT LCD monitor, via the digital DVI output of the Mac.

I thought I'd give Linux a go for the first time, and recently installed Ubuntu Warty on the machine (off CD). When I restart and boot off the hard drive it seems to load Linux, but most times I get a blank screen.

I've tried typing the following video arguments into both Open Firmware and Yaboot:

video=aty128fb:vmode:14,cmode:16
or
video=ofonly

About one time in every 20 boots it works, and I can see the command line of Linux, but when I restart using the same method it goes blank again. Drive me batty! :???: I don't think Linux likes those ATI 128 cards.

It never gives me any GUI. Should I do something to launch a GUI? Any hints on why most times the screen would be blank?

Thanks for any help.

---

### Post by DJ_Max on 2005-04-05
Well, it's the other way around, ATI has/had bad Unix support. You can try to reconfigure XFree86. I don't use Xfree86, so I forgot the command, something to the tune of:

sudo dpkg-reconfigure xserver-xfree86

---

### Post by Tofu on 2005-04-06
Thanks for replying, DJ Max.

I typed into the command-line:
sudo dpkg-reconfigure xserver-xfree86
as you suggested.

It seemed to indicate that xfree86 doesn't exist.

So then I typed in the following...
sudo apt-get install ubuntu-desktop

Then all kinds of files started downloading from the net.

Now, Linux boots up off the hard drive, but leaves me with a blank screen again. And this time I can't get to the command line. It's putting out some crazy monitor resolution like 3000 x 2 pixels.

So I can't see anything on the screen. But now I hear a cute little bongo drum noise when it boots up, which it didn't have before.

Is there any way to restore vision when you can't see anything?

---

### Post by Tofu on 2005-04-07
Update: replacing the new LG LCD monitor with an old CRT (tube) monitor solved the problem, and I can see the screen again.

Either the LCD monitor is more sensitive to incorrect screen resolutions, or possibly there is an incompatibility using the digital DVI output of the computer. The same monitor works fine with booting Mac OS X.

---

### Post by DJ_Max on 2005-04-07
The ubuntu-desktop is nothing but a meta-package, won't be helpful for your problem.

If you're using Warty, I believe you should have XFree86. Post your /etc/X11/XF86Config-4

If you're using Hoary (5.04), then you have Xorg /etc/X11/xorg.conf

---

### Post by 2cute4u on 2006-04-10
[QUOTE=Tofu]Update: replacing the new LG LCD monitor with an old CRT (tube) monitor solved the problem, and I can see the screen again.

Either the LCD monitor is more sensitive to incorrect screen resolutions, or possibly there is an incompatibility using the digital DVI output of the computer. The same monitor works fine with booting Mac OS X.[/QUOTE]

I'm having the same problem. I have the same Mac, but unlike you I don't have a CRT. did you ever get your DVI LCD working?

---

