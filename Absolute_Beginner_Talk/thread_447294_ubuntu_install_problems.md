---
title: "ubuntu install problems"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by earlgrey888 on 2007-05-17
new to linux, ubuntu, etc.

i'm working on installing ubuntu on an old laptop (toshiba satellite a15-s127) from the desktop cd (downloaded and burned it)

after choosing "start or install ubuntu" from the menu, it goes through a list of things and says "OK" to all of them except:

1) loading hardware drives
---> instead of OK it says: "intel_rng: FWH not detected"

2) configuring network interfaces
---> says "OK" but underneath it has a few lines of: "cat:/var/lib/acpi-support/........: no such file or directory"

anyhow, after this, the screen alternates between either being completely dark or completely orange or orange with ubuntu in the middle with an error box at top left saying "there was an error starting the GNOME Settings Daemon. some things, such as themes, sounds, or background settings may not work correctly..."

and, uh, it stayed this way for about 1.5 hours... and i tried again a few times, but same problems...

anyhow... if you know how to fix this or if it can be fixed that would be awesome! thanks.

also-someone said the problem could be that my graphics card (i think it's only a 64mb intel one); is this true? if so, is there anything i can do to make ubuntu work on my laptop?

---

### Post by n8bounds on 2007-05-18
seems like a bug in the kernel you are using (u are trying edgy right?)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982)

try edgy or dapper and see if you get the same results

also try reading

[http://www.linuxquestions.org/questions/showthread.php?t=504032](http://www.linuxquestions.org/questions/showthread.php?t=504032)

then again it could just be a bad kernel module for ur HW

[http://www.linuxquestions.org/questions/showthread.php?t=546360](http://www.linuxquestions.org/questions/showthread.php?t=546360)

but you havent even got it installed, so you cant change whats not there

does the alternate install cd do the same thing?

---

### Post by trent dillman on 2007-05-18
...

---

### Post by earlgrey888 on 2007-05-18
Alternate CD worked, and everything appears to be working. :-) Thanks!

---

### Post by n8bounds on 2007-05-18
awesome!  I don't much about how it works, but I would guess the alt. cd doesn't try to load as much as the live cd when all you want to do is install.  Perhaps the live cd image is subtly different than what you get when you boot from what it installs to disk...

---

### Post by led_scorched on 2007-05-22
I've used the same Laptop, and installed Hoary and Dapper both with no problems.  I added some ram (making it 512 now) but thats it.  I doubt its a capatibility problem - unless they made each batch of them with the cheapest hardware that week. (?)

---

