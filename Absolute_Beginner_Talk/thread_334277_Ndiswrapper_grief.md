---
title: "Ndiswrapper grief"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by blore123 on 2007-01-08
Hi,

For those of you who read my last thread - it's more trouble I'm afraid...

I have reformatted my HDD and now put Ubuntu 6.10 on it using the Double-sided LXF DVD that you get with Jan. 2007 edition. This is the 'edgy' version I think. With kernel 2.6.17-10 (generic).

Install for this is great, no problems at all, in fact it's now easier than Windows anything.

Problem is I have a Belkin F5D7001 PCI network card and my drivers work ok, but Ubuntu cannot seem to 'see' the hardware. This isn't a problem I've ever had before. I'm 99.9% certain the wireless card is fine, having used it yesterday on XP. Ndiswrapper also shows no errors in the make process. However, I picked up on the probable lack of hardware detection when:

1. Card's lights failed to glow in any way at all.
2. ndiswrapper -l returned driver details only (ie. no 'hardware present' message)

Can somebody tell me what I'm doing wrong?

Thanks :)

---

### Post by Sandlst on 2007-01-08
I had this problem in Breezy (2 releases ago) and I was able to fix it by appending ```
pci=assign-busses
```to my kernel boot options, I am pretty sure they have made this procedure obsolete in the new versions, but I suppose it is worth a try.  To do this, open a terminal and put in ```
sudo gedit /boot/grub/menu.lst
```Find the first kernel line (scroll to the bottom and then go up until you find the highest line without a # in front of it) It will look similar to this:

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-686 root=/dev/md1 ro quiet splash [COLOR="Red"]pci=assign-busses[/COLOR]
initrd		/initrd.img-2.6.15-27-686
savedefault
boot

add the part in red at the end of the line, with a space before it, then reboot and hope!

---

### Post by blore123 on 2007-01-09
Thanks for that, it does seem that I have sound back on my machine, however, still no hardware present on ndiswrapper -l and still no wlan0 detected as a result (trust me, it's there).

Funny thing is, I was using Breezy Badger Ubuntu before too, and this was about the only thing I could do with any proficiency, and I never remember having to add lines into the code. (Although I do like having my s/card working again :))

Any other ideas folks?

---

### Post by Titus A Duxass on 2007-01-09
What does the command "lspci" return?

---

### Post by blore123 on 2007-01-09
I believe the only relevant line (as a lot of stuff is listed here) is as follows:

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I do understand Belkin use Broadcom chipsets, so I guess this must be the card. Is this any help at all to you?

---

### Post by Titus A Duxass on 2007-01-09
Okay, so your card is recognized in some way by your pooter.

Have a search around the forum for "broadcom", there are lots of threads that may be of help.

Good luck with the challenge.

Try this one for starters:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)

---

### Post by blore123 on 2007-01-09
Ok, this is a bit wierd...

I ran one of the other forums help guides to start up the card and it did not much (again)

However, more careful reading of the iwconfig table revealed two things:

1. I *really* ought to read these things more carefully, as they clearly aren't just there to make Linux look more geeky and stuff.
2. An AP going by the name of 'eth0' is present, under a differing ESSID and Nickname, but with the same chipset at the heart of it (Broadcom) and using the same WEP key (that's a random 128-bit key, so I do *not* think it is chance).

I'm going to try logging onto it, although the words Access Point: Invalid do not inspire me with much hope, any ideas on how my AP got changed to a new name and switched to Managed Mode, instead of Enabled...?

---

### Post by Titus A Duxass on 2007-01-09
Have you disable any on-board hard-wire devices?
Have you tailored your interfaces file to auto wlan0 or whatever is required with Broadcom devices?

---

### Post by teaker1s on 2007-01-09
worth a look

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by blore123 on 2007-01-09
For anyone who reads this and thinks 'not another Broadcom guy who's being told to read the forum' - I have managed to correct the problem perfectly, in fact I'm posting this thread off Ubuntu now using the card!

The thread I ended up using is [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) and there's just a guide on there, follow it to the best of your ability and you may have to restart the system a couple of times, but after that, wlan0 just appeared on my system when I checked it out in System > Adminstration > Networking

Thanks for all of your help all those who posted replies - I really feel that I'm going to get plenty of help with my new OS along the way, and who knows - a few years from now, maybe I'll be able to help another user on here!

Thanks :)

---

### Post by Titus A Duxass on 2007-01-09
Glad to hear that you have succeeded.
Have fun.

---

### Post by blore123 on 2007-02-13
New problem:

Has anyone carried out the recent updates (12-FEB-2007) to Ubuntu and found that Ndiswrapper returns a FATAL when you modprobe it?

I do, and it is causing increased use of a certain M$ OS as I need wireless.

Help!

---

