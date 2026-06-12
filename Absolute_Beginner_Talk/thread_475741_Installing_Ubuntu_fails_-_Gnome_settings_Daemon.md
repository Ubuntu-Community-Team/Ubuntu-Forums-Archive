---
title: "Installing Ubuntu fails - Gnome settings Daemon"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Pconfig on 2007-06-16
Hey,

I'm currently switching over all my computers to Ubuntu. The installation on those systems went fine everywhere. But I'm currently having problems to install it on an old Dell. It's a dell with a 1.4GHz cpu and 256mb ram. Should be enough for ubuntu.

When i try to boot from the live CD i get the following error:

```
There was an error starting GNOME Settings Daemon

Some things , such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: The remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Then i still see the ubuntu windows that's loading nautilus and such but after that i get a "black" screen. It's not white but the ubuntu color and there are no icons / bars on it. Anybody an idea on what causes this problem or how i could find what's causing this problem?

Thanks in advance

---

### Post by Brightbelt on 2007-06-16
I had a similar problem once, and I realized after the install that it never asked me for a user name or a password.  I tried installing again and it worked the second time. 

I'm no Linux expert by any means and I'm still a beginner, but I've had plenty of experiences with reconfiguring my xserver on Ubuntu and it seems like what's happening to you is very similar to what happened when I tried installing my accelerated graphics driver and it rebooted to a blank screen. 

I would try using a different disk and/or try burning a disk at a lower speed (maybe like 2x or 4x).  Also you might try using a Text-based install CD. On the Ubuntu download page, right next to the install now button, there's a box you can check that gives you a text-based/alternative install CD.

I hope this helps, Frank B.

---

### Post by neutrin on 2007-10-14
when I try to install ubuntu 7.04 or 6.10, I receive the same message:

[FONT="Courier New"]"There was an error starting GNOME Settings Daemon
Some things , such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: The remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in."[/FONT]

After that i close the error message the ubuntu desktop appear with all its tools. But when i try to install Ubuntu using the "Instal" button it does not work.

I have an Acer Aspire 3613 WLMi
[I]* Intel Celeron M processor 370 (1.5 GHz, 400MHz FSB, 1 MB L2 cache)
* 60 GB HDD
* 256 MB DDR2
* OS: Windows XP[/I]

If there is someone who know how to resolve this prblem, give me an advise.

---

### Post by Pconfig on 2007-10-22
Installing ubuntu using the alternate cd fixed the problem for me back in the days :)

---

