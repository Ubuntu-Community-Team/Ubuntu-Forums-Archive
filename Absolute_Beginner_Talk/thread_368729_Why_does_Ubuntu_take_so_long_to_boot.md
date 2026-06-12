---
title: "Why does Ubuntu take so long to boot?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by gkimberwhite on 2007-02-23
I just installed Ubuntu 6.10 on one of my computers and love everything I've seen so far except for the fact that it seems to take forever to boot (although it shuts down quickly).  One of my friends suggested disabling unneeded services, which I have done, but that doesn't seem to make a significant difference.  Does anyone have any thoughts or suggestions on how to speed up the booting process?  Thanks!  :confused:

---

### Post by meng on 2007-02-23
Press alt-f1 during boot and see if you get error messages.

---

### Post by Spr0k3t on 2007-02-23
System here boots very fast by comparison to the alternative.  Even my slower laptop boots faster than my very updated desktop system with windows.  What is your system configuration?

---

### Post by K.Mandla on 2007-02-23
How long is too long? If you're using an old, old machine it could take well over a minute to get things going. On the other hand, there are ways to make it go faster.

P.S.: Welcome! :D

---

### Post by Sef on 2007-02-23
What are your system specs, especially CPU and RAM?

---

### Post by neji on 2007-02-23
how about trying to unplug USB devices? my system hangs at boot if I have my memory card reader plugged in, but works fine if I plug it in after everything else loads

---

### Post by chr on 2007-02-23
a low amount of ram is often the reason for a slow boot process.

---

### Post by gkimberwhite on 2007-02-23
My system is P3 at 700something MHz with 512M RAM (it's a little older but it shouldn't have problems).  I'll try the F1 idea when I get home.  Any other suggestions?

---

### Post by gkimberwhite on 2007-02-23
I've tried reinstalling a couple times and it's always the same experience - not much faster than booting off the live CD.

---

### Post by gkimberwhite on 2007-02-23
So my config is exactly P3 734 MHz, 512 MB of RAM.  Any ideas why it would take a couple minutes to boot up?

---

### Post by Spr0k3t on 2007-02-24
Sorry it took so long to reply.  I've timed my booting for you to compare to on most of my active systems I have.  Here's the rundown.

AMD 64 FX2 Desktop system (2GB mem): 26 seconds from cold, no grub, clean install
Alienware Pentium D, 2GHz Laptop (1GB mem): 30 seconds from cold, no grub, clean install
Dell X1 Centrino 1.6GHz Laptop (1GB mem): 37 seconds from cold, no grub, clean install
Gateway E-4200 1.5GHz Desktop (512MB mem): 53 seconds from cold, no grub, clean install
Compaq E500s 800MHz Laptop (256MB mem): 1m 28s from cold, no grub, clean install

The install covers Ubuntu Edgy Eft with all the latest updates with multiverse/universe inclusive.  The first system would more than likely boot faster than 26 seconds but I've got some extra services I've installed.  I'm wondering if your bottleneck isn't the drive itself.  What kind of buffers are on the drive and how is the drive formatted?

---

### Post by hardyn on 2007-02-24
does the hard disk activity stop for a period? does is seem like it might be waiting for something to time out? or does the hard disk run constantly?

---

### Post by waynejkruse10 on 2007-02-24
This is actually a very interesting topic as I was looking at this just yesterday.

I have a Dell Inspiron 6400 (Core 2 Duo, 1gb Memory, 120gb 5400RPM), certainly not slow by todays standards. On it I have a dual boot Ubuntu 6.06 and Windows XP SP2. I decided to time the booting process to compare.

I timed from Grub to Login as that is how both systems are configured, XP sits at the login screen and so does Ubuntu.

Ubuntu: 38.8 Seconds
XP: 20.5 seconds

That is interesting to say the least, does anybody know how to speed up the boot process?

By the way, my mother is loving Ubuntu (even though she can never pronounce it right :p), I doubt she notices the longer boot though.

---

### Post by K.Mandla on 2007-02-25
> **gkimberwhite said:**
> So my config is exactly P3 734 MHz, 512 MB of RAM.  Any ideas why it would take a couple minutes to boot up?
It could just be that Ubuntu is too heavy a desktop for the machine. I've used Ubuntu on 1Ghz machines and thought it sluggish, so you might be getting the same impression on a 733Mhz.

Have you looked at Xubuntu? Or perhaps a lightweight system like the ones in the wiki? ... [uwiki]Installation/LowMemorySystems[/uwiki]

Don't forget that there are speed limitations for hardware, too. A faster hard drive or a faster grade of memory might improve things. But don't start dumping money into your computer yet. See what a lighter desktop does for you first.

---

### Post by K.Mandla on 2007-02-25
> **waynejkruse10 said:**
> Does anybody know how to speed up the boot process?
Ubuntu's boot times are a long-standing complaint. If you want to get an idea or two for speeding things up, try [this thread]("http://www.ubuntuforums.org/showthread.php?t=206022") as a starting point.

---

### Post by Spr0k3t on 2007-02-26
Wow, you're kidding me.  The last time I tried Linux (days leading up to gnome/KDE), the boot times were like trying to load XP onto a system with 64MB of memory.  I'm happy with the boot times i have currently.

---

### Post by freelancer1995 on 2007-02-26
> **gkimberwhite said:**
> I just installed Ubuntu 6.10 on one of my computers and love everything I've seen so far except for the fact that it seems to take forever to boot (although it shuts down quickly).  One of my friends suggested disabling unneeded services, which I have done, but that doesn't seem to make a significant difference.  Does anyone have any thoughts or suggestions on how to speed up the booting process?  Thanks!  :confused:

XP is designed differently to Ubuntu.  Ubuntu starts services during boot up and XP will still be starting services, when the login screen is displayed, so, when you login it can fail to find resources, network setting, etc.  In fact, most windows professionals disable this quick boot option for XP because of this, I know that I do.  This also applies to Windows Servers and it is recommend you waiting up to five minutes before logging onto them to perform system tasks, just in case something hasn't started correctly.

---

### Post by Doomedelite on 2007-02-26
I must be the only one here who's Ubuntu starts up faster than XP...

---

### Post by coxc24 on 2007-02-26
I had a similar issue with my laptop and resolved it my removing the spash screen. You can do this by editing your Grub menu.

Edit the file /boot/grub/menu.lst

Remove anything after the 'ro' on the Kernel line. The 2 words are 'quiet' and 'splash'. I would tell you the exact line but only have access to a Debian box while at work. This will remove the spash screen and display everything that happens at boot, the same as ALT F1. This resolved the issue for me.

The only problem is whenever you update your kernel, you have to edit the menu. Not ideal but it works.

---

### Post by energiya on 2007-02-26
Compiling a kernel could save some boot time and give more performance. This made my PC boot 12 sec faster. Because of the quite low CPU power of the PC you are talking about, compiling a kernel on it wouldn't be recommanded (it will take about 2.5 hours or more), but if you have more horse power on another you can do the nasty part on it and just copy the new kernel to your PC.
You could also try [this]("http://ubuntuforums.org/showthread.php?t=254263").

---

### Post by gkimberwhite on 2007-03-05
Thanks, everyone.  Lots of good suggestions to try (and maybe a dose of reality to accept about the speed limitations of my hardware).

- G

---

