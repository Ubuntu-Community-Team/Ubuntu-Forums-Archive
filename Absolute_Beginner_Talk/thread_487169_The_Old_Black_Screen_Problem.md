---
title: "The Old Black Screen Problem"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Gipper P on 2007-06-28
I seem to be having the same problem as many people on this board, but no luck with the replies that have been given to them so far and I will therefore clarify my position to see if there is anything different for me to do.

I installed Ubuntu 6.06 on my system, and that worked fine. I then decided to upgrade to 7.04 and therefore had to upgrade to 6.10 first. This happened without any problems: it only said that some packages weren't going to be supported. This happened again for the 6.10 -> 7.04 upgrade.

Now, once I start the 7.04 version, I get the ubuntu loading screen, with the logo and the progress bar. After this the screen is just black. The monitor light is still green, indicating that it is still receiving some kind of signal.

Starting in recovery mode and using 'startx' creates the same situation.

The computer that I am installing it on is a Pentium 4 2.8GHz, 512MB RAM, 60GB HDD, 128MB Ati Graphics.

Is there anything I can do to stop these blank screens?

Many thanks in advance for your help.

James

---

### Post by ecs_pf5 on 2007-06-28
removing "quiet splash" from the relevant line in grub's menu.list did the trick for me but it sounds like you have a slightly different problem.. since I was getting nothing but blackness from the start. might be worth a try though.

I'm suspecting my ati card of many horrible things ATM, think I'm going to get rid of it soon :(

---

### Post by anewguy on 2007-06-29
It's possible that either the xorg.conf file got replaced on the update, or that your driver "broke" on reinstallation.  I say this because it would appear to be an X isue, and I seem to remember a post by gcos7 back a couple of weeks ago about his video and that when he did the upgrade to 7.04 he had to redo his X video driver after the update.;)

---

