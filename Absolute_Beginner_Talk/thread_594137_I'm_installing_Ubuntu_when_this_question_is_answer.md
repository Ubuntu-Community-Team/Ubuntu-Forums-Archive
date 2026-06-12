---
title: "I'm installing Ubuntu when this question is answered"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-27
How can I have Ubuntu not auto-detect my graphics card on my first boot?  I have an Ati 9500 Pro and the open-source drivers crash it immediately.  The proprietary drivers in restricted drivers manager work, so I want to boot into vesa on first boot and install those instead of the open source drivers.  How do I do that?  I won't be able to access the forums if I have problems during install without walking across campus to the lab, so I need to know now.  Thanks.

As long as I'm at it, will an external HDD automatically mount when I hook it up?  It's USB.  I know my flash drive mounts automatically so I assume it's the same for the HDD.

---

### Post by Kosimo on 2007-10-27
You can start Ubuntu from the CD using (Safe Graphics mode)  Did u try it?

On the other hand you can always download the alternate installation disc.

Don't give up!

---

### Post by sochbat on 2007-10-29
When you start up, disable xserver, and try this.

sudo dpkg-reconfigure xserver-xorg

Should bring you to a walk-thru menu, asking what driver you want to use, other random questions.

Check out YouTube for a video if you're confused.  Try searching 'splitpaw xserver'

Bingo, found it.

[http://youtube.com/watch?v=-RvqcKDpQdo](http://youtube.com/watch?v=-RvqcKDpQdo)

He's got some awesome videos.  If he's here, I say hello!

---

