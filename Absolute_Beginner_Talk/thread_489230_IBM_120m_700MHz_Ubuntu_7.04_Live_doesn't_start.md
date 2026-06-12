---
title: "IBM 120m 700MHz: Ubuntu 7.04 Live doesn't start"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Katz on 2007-07-01
Hi all,

I am a firsttimer to Linux isntalling. I have a IBM a20m 700 MHz laptop. I can't get the Ubuntu started at all from the LIVE cd.

Here is what happens:

First possible error:

During initial loadup i get this message:

> IBM system detected this module may corrupt your serial eeprom refusing to load module

The loading seems to continue regardless of that, but this pic is where it seems to get stuck:

[[img]http://xs117.xs.to/xs117/07260/Nautilus.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs117&d=07260&f=Nautilus.jpg)

Here is the Error message:
> 
There was an errors starting  the gnome settings daemon.
Some things such as themes, sounds, or background settings may not work correctly.
The last error mesage was:
Did not receive a reply. Possible causes include: The remote application did not send a reply,
the message bus security policy blcked the reply, the reply timeout expired,
or the network connection was broken.

GNOME wil still try to restart the settings Daemon next time you log in.

I can somewhat move the cursor at this stage, but sometimes it moves and some times it doesn't. I can't click the CLOSE-button on the error message due to this problem.

If I just let it run, the screen will eventually turn blank (whitish background) with nothing on it and the CD-drive seems to stop.

Background:

1. I had an old XP-version running on the laptop. This same thing  happend with it installed on the laptop.

2.I used DBAN to wipe the harddrive to get rid of the old XP installation., but this same thing seems to happen this time too.

What should I do?

I have the GParted LiveCD available, shuold I just try to reformat/partition the harddrive or do you guys have any other suggestions?

-Katz the total Linux beginner

---

### Post by bigken on 2007-07-01
you can use gparted liveCD to format the hdd you might need to flash the bios

you could also try the alternate CD

---

### Post by bigken on 2007-07-01
how much ram do have you need at least 250mb to run the live cd

---

### Post by Katz on 2007-07-01
> **bigken said:**
> how much ram do have you need at least 250mb to run the live cd

AHH, that could be the problem. I only got 192 mb. I actually read that it's the minimum recomended amount, not even minimum required. Didn't notice that the Live requires more.

Can I use the Alternate Installation CD then?

Oh well, I'll try the GParted and the alternate CD.

---

### Post by bigken on 2007-07-01
ye just install from the alernate cd good luck ;)

---

### Post by Katz on 2007-07-01
After a few unsuccesful tries to boot from the Alternate disc, I removed and reinesrted the battery of the laptop and the Alternate CD booted without problems.

Ubuntu is up and running, but doesn't seem to be able to turn the lap top off. It stays in the ubuntu startup screen (black screen with Ubuntu Logo and Ubuntu text).

Anyways, gotta go shopping now and look into it later.

Thanks!

Katz - Ubuntu up and running

---

### Post by bigken on 2007-07-01
remove the disc and hit enter

---

### Post by Katz on 2007-07-02
> **bigken said:**
> remove the disc and hit enter

There was no disc in the drivebay. Could be something in the BIOS or does Ubuntu have something similiar with WinXP's power management settings where you need to give the system a permisson to turn off the computer through software?

My next problem is getting the wireless Buffalo G54 card to work. Haven't had a chance to do anything else, but insert the PCMCIA card into the laptop. Well, have to work on that after I get home from work.

Katz

---

