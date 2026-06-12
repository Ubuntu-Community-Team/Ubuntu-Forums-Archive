---
title: "Can't boot from CD either"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by samienela on 2007-01-06
Hi, I am  having problems booting from the live CD.

The machine is a custom build - my first - a Frankenstein mix of new, used & legacy components - an old machine in which I installed a new HDD and put in a video card.

This is also my first Linux experience.

Mobo:  Gigabyte 7VT 600 1394 (socket A) dual BIOS board
CPU:  Athlon 2800+
HDD:  IDE, 80 Gb, virgin, empty, formatted by a Mac with "MS-DOS" formatting (not sure what that means exactly, as I know there are at least two formats, NTFS and FAT)
RAM:  2 x 512 Mb DDR 400
Original CD drive: 16x 10x 40x 
Current CD drive: 52x 32x 52x "does everything" drive
Videocard:  Diamond Rev P Multimedia, a pre-Y2K PCI videocard from a PII machine, but it gives me a screen image
Monitor:  Apple studio display (CRT) 
Network adapter card:  Netgear WG311v2 rev A1

I burned the i396 iso CD on my Mac mini at work
I set the BIOS to boot first from the "CDROM"  - all other settings are default.
I thought the CD drive might be having problems so I swapped in a newer one. No joy.

OK, here's what happens when I try to boot.
Sometimes the machine hangs up at some kind of validation task before the liveCD startup screen, but if I power it down and unplug it for a few minutes it behaves better.
Occasionally I get the live CD's startup choices screen and it starts launching and hangs partway through the list of startup tasks.
Usually I get the live CD's startup screen and it goes all the way through the long laundry list of boot tasks, then the screen shows an underscore for a moment, then it goes blank.

A friend told me that I have to hit any key when I see that underscore.   I've tried to do that, and once it did boot up into the Linux desktop, but usually the screen just blanks.

Burning questions -

What am I doing wrong?
Is it a hardware issue?  
What do I have to do after that underscore appears?  Shouldn't the desktop just come up by itself the way it does in OSX and Windows? 
Is there a way to recover from the blank screen?  a function key, escape, something else?   Currently it's a dead end for me and all I can do is power down the machine... from the front panel :( 
 
You guys have been so kind to toadman46, please help me too.

---

### Post by Spin Doctor on 2007-01-06
Did you try burning your liveCD with the lowest possible write speed? Burn on lowest available speed on your highest quality CD. This could solve your problem if you are lucky =) If not, try burning your ISO Copy from a different computer too.

---

### Post by jvc26 on 2007-01-06
The other question would be whether you md5 checksummed the disc when you downloaded it - that would tell you whether there are any errors in the download, and the disk check that Spin Doctor mentioned will tell you if there were any errors with writing the disc.
The md5 checksum information is in a post on installing ubuntu - am afraid I dont have the link, but I'm sure a forum search will help if you're not sure what it is :)
Il

---

### Post by samienela on 2007-01-06
So you want me to eliminate the possibility of CD problems first?  Hmm, OK. Bear in mind that when the disk was burned, it was verified as being OK by Disk Utility (the utility that MacOSX 10.4.8 uses to burn CD's)  And I'll check the checksum too. 

On the other hand, I don't understand how an error on the CD could be responsible for such a wide variety of aborted bootups plus the one successful full boot to the Gnome desktop.

Just to be sure, I'll stop by work tomorrow and burn another CD.  In your opinion, should I stick with 6.06 or go to 6.10?  I expect that once I get ubuntu running and installed, the next big hurdle will be connecting to the wireless network (an Apple Airport Extreme system).  Does either version hold an advantage in wireless networking?

Meanwhile, is there anything else you can suggest?  In particular, is there any way to get into command line mode from the prompt that appears briefly before the desktop is supposed to load?

---

### Post by Westies on 2007-01-06
> **Spin Doctor said:**
> Did you try burning your liveCD with the lowest possible write speed? Burn on lowest available speed on your highest quality CD. This could solve your problem if you are lucky =) If not, try burning your ISO Copy from a different computer too.

I'm pretty sure that burning on the lowest available speed is actually pretty bad.

---

### Post by kinematic on 2007-01-06
> **Westies said:**
> I'm pretty sure that burning on the lowest available speed is actually pretty bad.

it is.
a relative of mine works at the research department of TDK and i asked him about burning once.
he told me that modern good quality cd's/dvd's don't like extremely slow speeds and that if you use a good quality cd/dvd and it throws up errors after burning it's the cd/dvd burner that's at fault.
if you have a good quality burner and cd's/dvd's there's no need to go slower than 8x(he always recommends nec drives).

---

### Post by samienela on 2007-01-07
Hi folks - I downloaded the i396 iso again, burned it to a virgin CD-R, verified that the checksums matched, and it's giving me the same results.  The desktop still won't boot up from the live cd - the machine gets all the way through the boot tasks then blacks the screen.

I was able to get into the command line using Ctrl-Alt-F1, a workaround recommended in the "troubleshooting" section of the psychocats site.  

I tried installing from the command line but the instructions there are for installing from the alternate CD, not the live CD.  I tried running "aptitude" and selecting all available software for install - however, none of it installed, instead I got a long string of error messages, one for nearly every package I was trying to install:

[http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main vlan 1.9-1 [ERROR]
Temporary failure resolving ' archive.ubuntu.com'

If it's not the CD, what's going on?  Looking forward to some more opinions here.

Thanks!

---

### Post by riven0 on 2007-01-07
It's possible your network connection isn't working. When you get to the terminal, can you try pinging google?

> ping google.com

What does it return?

---

### Post by samienela on 2007-01-08
I know for sure that there's no network connection.  The one time it booted fully to the desktop it didn't have a connection, and I'm sure it doesn't now.  The box has a wireless card, and my home wireless network is Apple Airport.  

I'm writing to you from a different computer in the same room.

---

### Post by MkfIbK7a on 2007-01-08
> **kinematic said:**
> it is.
a relative of mine works at the research department of TDK and i asked him about burning once.
he told me that modern good quality cd's/dvd's don't like extremely slow speeds and that if you use a good quality cd/dvd and it throws up errors after burning it's the cd/dvd burner that's at fault.
if you have a good quality burner and cd's/dvd's there's no need to go slower than 8x(he always recommends nec drives).

yes burning at a very slow speed can actually be worse than doing it fast as in it melts parts of the cd and completely destroys it...

---

### Post by riven0 on 2007-01-08
> **samienela said:**
> I know for sure that there's no network connection.  The one time it booted fully to the desktop it didn't have a connection, and I'm sure it doesn't now.  The box has a wireless card, and my home wireless network is Apple Airport.  

I'm writing to you from a different computer in the same room.

Then that'll be the reason why you can't install any new packages. All the packages are downloaded from the main server, so you need a net connection. Otherwise, you can try Canonical's official site [here]("http://packages.ubuntu.com/edgy/") and download the packages manually, transfer them over to the Ubuntu comp and install them there. But taking care of the dependecies can become a problem.

---

### Post by samienela on 2007-01-08
Ok, I fixed it - what clued me to the problem was trying to run sudo dpkg-reconfigure xserver-xorg  as recommended in another thread in this forum.  When the list of video cards didn't even have "Diamond" listed, the :?: turned to :idea:.

After I took out the really ancient PCI video card (Diamond brand, from 1999 :) )  and put a Chaintech GeForce MX4000 card in the AGP 8x slot, the live cd booted on the first try and it's now installing ubuntu on the hard drive.

Case closed - the culprit was apparently the obsolete videocard.

---

### Post by noMoreWindows on 2007-01-08
[QUOTE=samienela;1977325]Hi, I am  having problems booting from the live CD.

The machine is a custom build - my first - a Frankenstein mix of new, used & legacy components - an old machine in which I installed a new HDD and put in a video card.

This is also my first Linux experience."
 
question is, is it a hardware... did you check the jumper setting of your cd drive. make sure it is set to MASTER. if it is hanging up (intermittent), pls check memory, it might be loose also check CMOS settings (f1 or del will let you in).

the easiest way to troubleshoot a hardware is elimination. if you think its a hardware problem. replace the harddrive with known good with OS installed. 

Am also new here and I got same problem earlier, the solution is the cd drive setting (was set to AUTO instead of MASTER)

goodluck

---

