---
title: "Boot from v6.06 LTS hangs"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by cypressotter on 2006-11-03
Running Windows, I insert the Live CD, the browser loads but I find no Install icon.
When I boot from the Live CD, the process begins, but seems to fail, with both the CD and HD seeming to swap info but nothing on the screen and no completion for an hour or two.

Any ideas?

IBM Thinkpad 600
300mhz P2
128mb RAM
4gig HD
Latest BIOS

---

### Post by Klaidas on 2006-11-03
Well, you shouldn't find any install button while using a browser in windows :)
You should boot the LiveCD and then on the desktop there will be an install icon, the one you're looking for.

If the CD is OK (did you check the md5sums?), I see the only one reason it doesn't work - your hardware.

I have a P4 1.7GHz, 512 RAM and it's sllloooowwwww. I suggest using the alternate install CD

---

### Post by dmizer on 2006-11-03
couple of things here.

first of all, this is a complete operating system.  it won't run in windows.

second of all, you're working with some ancient hardware.  which is fairly common with linux users, but is also sometimes fairly difficult.

are you planning to replace your windows install ... ie overwrite everything on your hard drive?

---

### Post by cypressotter on 2006-11-03
Klaidas:
Yes, now I understand I wouldn't see the install icon under windows, but I would when booting from the cd, (which I have been unable to do).

dmizer:
Yes, I understand what I'm dealing with - an OS, AND an ancient computer. And yes I want to dump Windows and fresh install Linux. I wonder with my hardware if I should be trying some other version of Linux (lighter)?

---

### Post by Klaidas on 2006-11-03
I'd suggest Xubuntu.

Well, actually, I'd suggest an upgrade, but if want to run something on that thing, and it has to be *buntu, then use Xubuntu :)

---

### Post by cypressotter on 2006-11-03
...and if it doesn't have to be *buntu?

---

### Post by HereInOz on 2006-11-03
Mepis is another light weight distribution.

---

### Post by dmizer on 2006-11-04
there are a huge amount of possibilities out there for you for low profile linux based os.  dsl for one.

here's one that's been working very well for me on very old equipment:
[http://www.ubuntuforums.org/showthread.php?t=98233&highlight=howto+ubuntu+lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=howto+ubuntu+lite)

i think xubuntu is probably going to be too heavy for your machine.

---

### Post by cypressotter on 2006-11-04
Thanks for the help!
I've got xubuntu 6.10-alt installed. First issue:
Display Prefs has no entry for 1024x768, which this laptop (ibm tp 600) natives at. I've googled but found nothing specific to the 600. Anyone have an idea on this?

UPDATE:
I ran "sudo dpkg-reconfigure xserver-xorg" in the terminal and manually set the bit depth to 16 for 1024x768 and problem solved. Found this the  	Ubuntu Forums > Ubuntu Release Assistance  > Main Support Categories  > Hardware & Laptops forum topic #96240.

---

