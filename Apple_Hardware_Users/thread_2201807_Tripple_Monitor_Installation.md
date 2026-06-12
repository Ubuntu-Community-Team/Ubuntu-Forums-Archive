---
title: "Tripple Monitor Installation"
date: 2014-01-26
forum: Apple Hardware Users
---

### Post by Brandon_MacEachern on 2014-01-26
Hello, I am using a Mac Pro Early 2008, with 2.8GHz Intel Xeon 5400 Harpertown CPU's, and 32GB of RAM, and is equipped with two video cards.  ATI Radeon 4870, and ATI Radeon 2600XT.

The monitors are configured as follows:
Radeon 2600 - Monitors 1, and 3.
Radeon 4870 - Monitor 2.

Positioned on the desk in the following order:  1, 2, and 3.  Kinda simple, right?  Monitor 2 is the primary screen.

Monitor 1 is HDMI, ASUS 1920x1080.  Monitor 2 is a Apple 27" Mini Displayport LED Cinema Display.  Monitor 3 is a Acer DVI, and I think 1680x1200 (I may be wrong on it's specs though).

In OS X this works just fine.  In Windows this works just fine.  (OS X installs on monitor 2, and Windows installs on monitor 3).

When trying to install Ubuntu 13.10 from DVD, monitors 1 and 3 came up with the Ubuntu logo while monitor 2 was blank.  Once the installer fully loaded, monitor 1 went blank also saying no signal, and 3 showed a blank menu bar with a mouse cursor and grey background.  It showed nothing whatsoever.

So since it was the only display to show anything at all, I disconnected monitors 1, and 2.  The installer when booted, showed up, and appeared normally as it should.  I let it install onto the HD and when it was time to shut down, I let it shut down, then reconnected all 3 displays.  (Because in my mindset, I felt that it wasn't showing the displays because the driver wasn't loaded for the installer.).  Booted up with all 3 connected, and display 1 and 3 once again showed boot, but 2 stayed blank..  Once fully booted, 1 went blank again, and 2 was kind of a repeat of the installation.

So I shut down, and disconnected 1 and 2.  Boot up, log in, got a desktop on monitor 3.  Awesome.  Connected display 1 when the system was on, and clicked Detect in the display preferences, and guess what, monitor 1 finally was detected.  Clicked Apply, but an error was presented to me.  It appears it can NOT enable monitor 1.  I disconnect monitor 1, and connect monitor 2, which is supposed to actually be my primary screen, and no matter what I try, I can not get Ubuntu to detect that it's there.

Linked is the monitor setup, and also the error message I am running into.

The error:  [https://scontent-a-mia.xx.fbcdn.net/hphotos-ash3/t1/1545087_10201459520754009_477938093_n.jpg](https://scontent-a-mia.xx.fbcdn.net/hphotos-ash3/t1/1545087_10201459520754009_477938093_n.jpg)

The setup of monitors:  [https://scontent-b-mia.xx.fbcdn.net/hphotos-ash3/t1/734446_10200996859267761_1085554532_n.jpg](https://scontent-b-mia.xx.fbcdn.net/hphotos-ash3/t1/734446_10200996859267761_1085554532_n.jpg)

Any ideas?  I'm at a loss.  I'm going to try pulling the video card running monitors 1 and 3 (ATI Radeon 2600XT), and forcing the primary to install and configure, hoping I can at least get it to function.

EDIT:  Any information you request I will try my best to provide.  Please remember, fresh install of 13.10 from a DVD downloaded just recently from Ubuntu's own website, and freshly partitioned and installed.  These results are literally directly after install.

---

### Post by QIII on 2014-01-26
[I]Moved to [B]Apple Users


[/B][/I]Hopefully you'll get better answers in this sub-forum.

Best wishes!

---

### Post by Brandon_MacEachern on 2014-01-26
> **QIII said:**
> [I]Moved to [B]Apple Users


[/B][/I]Hopefully you'll get better answers in this sub-forum.

Best wishes!
Thank you, I hope so too.  I am using Ubuntu on a MacBook Pro Early 2011, and it's working fine there (on it right now typing this).  I would like to see all my Apple products, shakened from OS X and brought to the light that is Linux.

---

### Post by Brandon_MacEachern on 2014-01-26
This may not look promising, so hopefully someone can chime in.

I pulled out the Radeon 2600, reset the PRAM on the Mac, and left only the 4870 and the 27" Apple LED Cinema Display (mini displayport), and what I see upon booting the installation DVD is, GRUB, then a purple screen with a small icon at the bottom, then blackness..  I hear it continue booting then make the ubuntu bongo sound to signify it finished booting the DVD, but the screen is still black.

Hmm, I may need to forget about this machine ever running Linux.  Sounds like it can't do it.

---

### Post by Brandon_MacEachern on 2014-01-26
Update:  I was able to install by plugging only a single monitor into the DVI port of one of the video cards.  Once installed, the second DVI port of the Radeon 2600 just won't work, period.  I can't get a single thing out of it.  If I however plug monitor 1 and 3 into the first DVI ports of both cards, I can now get a picture on both.

Ubuntu still will NOT use the 27" LED Cinema Display that is monitor 2.  It doesn't even acknowledge it exists.

---

### Post by Brandon_MacEachern on 2014-01-26
Ok so I stripped it down to just only the Radeon 4870 and the Apple 27" LED Cinema Display, the only monitor I can get going.

It shows grub, goes purple, then black.  Nothing whatsoever.

I'm at a loss, it's like Ubuntu doesn't even see this monitor, but in Windows and OS X it works fine without issue.

---

### Post by Brandon_MacEachern on 2014-01-26
No help guys?  :(  I really need this workstation running.  It's my personal and main computer.  If I can't get Ubuntu to even acknowledge my 27" LED cinema display exists, I will be forced back to the dark side that is OS X.

---

### Post by Brandon_MacEachern on 2014-01-28
Please?  Bare bones to the Mac Pro, ATI Radeon 4870 and an Apple 27" LED Cinema Display, I can NOT get a picture.  I see the purple screen with a man and what looks like a disc icon on boot, then blackness from there.

I really need this working.  I can't even give you a log file or anything because I just can't see anything.

---

### Post by Brandon_MacEachern on 2014-02-01
So I guess I am just SOL here?

Here is what I have found.  The open source Radeon driver does not support the 27" LED cinema display.  This bug is big on the 27" iMacs too.  Apparently never fixed.

I am using an ATI Radeon 4870.  FGLRX is not supporting that card.  Lastly, FGLRX legacy that does, doesn't support Ubuntu 13.10.

Based on the lack of even communication, I think it's clear this is going to go nowhere, unless I got a different monitor that is DVI, but I don't want to downgrade my screen just for linux.  I'll keep linux on my macbook pro.

---

### Post by Brandon_MacEachern on 2014-02-04
Since this seems to be related to the fact the monitor is mini displayport, I purchased a DVI to mini displayport adapter since no one can help me.

---

### Post by Brandon_MacEachern on 2014-02-07
Using a DVI to minidisplay port adapter worked, and I get full resolution too.

Case and point:  Open source Radeon driver does NOT support mini displayport.

---

