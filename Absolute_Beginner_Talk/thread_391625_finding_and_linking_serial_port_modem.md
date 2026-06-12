---
title: "finding and linking serial port modem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by RonKZ on 2007-03-23
Modems seem to be Linux biggest nightmare; I have been trying off/on for 3 years now to switch totally to Linux, have tried several distros, many different dialup modems, and the modem connection problems have overwhelmed me every time.  I make no claim to being handy with command-line stuff, but am getting the hang of it.  Using edgy x64 and like it way better than anything else I've tried.  The modem problem (again) seems to be all that's in my way now, and I MUST make it right to transition completely away from M$.  My only way onto the internet today is via a modem in XP box over network.

My current modem: Best Data v.92 serial modem 56sx92.  It works fine in XP, but in over a week of fussing it's still not working in edgy.  It has boiled down to that Linux hasn't linked to modem to any serial port.  

Device Manager (read only? - c'mon!) finds Platform Device (Serial 8250) and two 16550A-compatible COM ports, on dev/ttyS0 and dev/ttyS1.  Only the ports, not the modem connected to any of these.  The modem shows lights only for PWR and DATA, never more.

GnomePPP reports only "modem not responding" on either S0 or S1, regardless of how it's configured.  Useless.

The Best Data CD contains a PDF with setup instructions using KPPP, which I've followed several times but they don't work.  This may be because Ubuntu runs the Gnome interface and thus all KPPP components aren't available, in particular khelpcenter.  Also, KPPP does not limit itself to SU, so one can't be sure it's really able to write some ?? config file.  I just now ran terminal:  sudo kppp   and think I have attached a copy/paste text file ???, but that did show a rash or problems.  Anyway, I have tried kppp every conceivable way without success.  Query Modem returns 8 ATI blanks.  It does, however, seem to recognize that THERE IS modem despite that it can't make it run.

So I then went thru all the scanModem rigamarole, finally getting the expected nadda because I have no win/linmodem attached.  There went another day.

Since, I've managed to find/download/install both setserial and minicom.  Sorry, but running those seems to be beyond me, hopefully someone can help?  thanks much.

Ron

---

### Post by rccharles on 2007-03-24
> **RonKZ said:**
> 

My current modem: Best Data v.92 serial modem 56sx92.  It works fine in XP, but in over a week of fussing it's still not working in edgy.  It has boiled down to that Linux hasn't linked to modem to any serial port.  

Ron

Perhaps you have the wrong name for the modem.  I didn't have luck with /dev/modem.  See if you can find the device name in the startup log. Power on your modem then your system and boot up.

Find out the name of modem.
dmesg >seedmesg
gedit seedmesg

look for modem  or tty
There is a find command in gedit control-f ( I think. )

Hopefully you will find something like ttys0.

If so, you device name will be /dev/ttys0

Robert

---

### Post by ieee488 on 2007-03-24
I don't use my external modem because my internal modem works with Linux.

But I did try out the external modem when I first bought it on eBay.

Anyway, I'm not keen on using /dev/modem.

I use wvdialconf to find the actual port, /dev/ttyS0 or /dev/ttyS1 or whatever and use that instead.

You may be surprised where Linux finds your modem. In Ubuntu 5.10, my internal modem was found at /dev/ttyS14. In Ubuntu 6.06, it's somewhere different. Same PC.

---

### Post by RonKZ on 2007-03-25
Well, yesterday was a huge day for a this newbie.  Spent about 4 hours in chat with a lady who has been using linux something-else for years, and she talked me thru several commandline things, I sent her output reports, yadda yadda.  We never could the the 56SX92 working despite all that, but we learned a lot, or at least I did.  

Meanwhile a 3CP5610A PCI hardmodem arrived. and as we needed a break from that long chat conference, I decided to shut down, stick the 5610 in, check my MB manual for ideas.  During that, I also moved this serial modem from the com2 to the com1 connection, went into BIOS and disabled the com2 port, booted into XP which installed on bootup the PCI modem and had to reinstall the serial modem to the other port.  XP wasn't running very well, but each modem connected at about 34bps.  After some XP fixing I rebooted to XP and each modem connected then at 49.2bps.

So reboot with Edgy, in safemode first, reboot again normal.  I don't know how much help safemode provides in linux, it just seemed prudent, okay?

Then edgy didn't show the PCI hardmodem but WOW - BUT gnome-ppp found the external modem, now on ttyS0, and after checking settings it actually *dialed*!!!  Well at that point it would hangup immediately upon being answered, but at least it was alive.  I had been concerned about mis-configs conflicts from using all these tools, gnome-ppp, kppp, setserial, minicom...  and sure nuf!

Now, thanks to posts by rccharles & ieee488, I fumbled a bit with wvdialconf.  That seems to have both cleaned up (yes, mis-configs) stuff AND found the 5610 as ttyS2, so it looks like I can finally get on with life and living!

Main thoughts.  The Best Data v.92 56SX92 external serial modem must have internal settings which don't accommodate being on the "wrong" COMport.  Mixing apps which mess with this stuff can cause problems.  While kppp seems a good tool, it appears to build conflicts with gnome-ppp.  Setserial and MiniCom -- you better know what you are doing -- I don't pretend to know!!!  Linmodems?  yet another world, get out your hammer & forget them!

Final thought.  Yes, I realize dialup users are a smaller percentage these days, BUT there are still lots of people in this world who have no alternative.  I have 20+ years of quite intense dos/windoze computing, but not a programmer.  I now build/rehab computers as a retirement pastime, and they'll all be sold/resold with Linux OS.  Over the past 3 years I have tried and given up on several distros because I couldn't grasp the linux language/approach, thus I'm still a newbie on the bottom rung of this latter.  Every time, every distro, dialup modems are a huge problem.  Most of my prior experience is either useless or even a barrier to success with linux.  Today, Ubuntu Linux is better than winXP in so many ways.  But if we're gonna kick M$ out of our bed, we need to be clear as a bell on dialup how-to.  Newbies might spend a few hours, but spending days will make most anyone go bye-bye.

---

