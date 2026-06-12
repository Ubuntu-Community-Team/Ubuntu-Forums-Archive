---
title: "With bated breath..."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by WJason on 2007-08-31
A friend introduced me to ubuntu a few months ago.  I booted a live CD version on a PC at work and immediately fell in love.  However, ubuntu failed to recogize the video adapter on my Sony Vaio VA10G at home. :-(
So, I waited for 6.06 to come out.  No joy.  I was thrilled when 7.04 was relased; but, still no joy.  I've tried all the workarounds suggested here but nothing works.  I'd love to run ubuntu; but I'm forced to go with one of the other flavors of Linux (all of which have booted just fine on my Sony Vaio VA10G).   Knoppix is looking like my second choice.

Will ubuntu be supporting the Sony Vaio some time in the future?

---

### Post by marx2k on 2007-08-31
What video card is it using?

---

### Post by WJason on 2007-08-31
ATI Mobility Radeon X700 w/256MB Video memory

---

### Post by marx2k on 2007-08-31
And you've done the standard 'sudo dpkg-reconfigure xserver-xorg'?

Have you tried ATI's proprietary drivers? 

Is it a 64 bit card?

A few days ago, I brought my USB drive with Fiesty installed on it over to school where they have 64 bit ATI cards and I had to do a few things to get it to work correctly.  Are you using the fgrlx driver? 

Can you describe what youve done so far, what drivers you are using, what sort of monitor?  

Post your /etc/X11/xorg.conf
Post your /var/log/Xorg.0.log

---

### Post by WJason on 2007-08-31
I haven't tried 
```
sudo dpkg-reconfigure xserver-xorg
```

If I recall correctly, I tried something like "api" and "noapi".  Took me forever to figure out how to get to the command line for ubuntu  LoL
Which reminds me:  Although ubuntu presents me with a totally blank screen after booting I did discover that I can bring up a command line with the, hm.....  is the F6 key?

Sorry for being vague but after many attempts a couple months ago I gave up and haven't tried anything until I got 7.04 a few days ago.  I figured if it didn't "just work" on bootup then I would just frustrate myself trying anything else.  But, I will try your suggestion when I get home later today.

64 bit?  I don't know; the spec isn't specific.

How would one use a proprietary driver with a live CD?

The Sony Vaio is an all-in-one with a built-in 20" wide LCD monitor (wide format).  It also uses wireless keyboard and mouse (I think they're bluetooth; but I'm not sure).

---

