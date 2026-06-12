---
title: "Feisty- ATI screwup"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by miznatt on 2007-04-25
I upgraded to feisty from edgy and experienced bad lagging, and after some forum lurking I tried the ATI card HOWTO: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Well upon reboot, I am told that Xorg cannot load and the gui cannot be displayed, leaving me with just a command prompt...

I'm not sure how to revert this, and whether or not it is more beneficial for me to fresh install feisty, but will I risk losing the files saved on the box? I am on windows as I dual boot, so any help is greatly appreciated, thanks!

---

### Post by mills on 2007-04-25
try this code

sudo dpkg-reconfigure xserver-xorg

hope it works

---

### Post by 007Bond on 2007-04-25
Your installed Xorg / ATI driver is set for your old kernel it needs to be run again and reconfigured.

---

### Post by guardsman85 on 2007-04-25
I had the exact same problem.  After you reconfigure X (see Mills' post two above mine) you could try the instructions at [*http://tinyurl.com/2wv7jd*]("http://tinyurl.com/2wv7jd")

This was the only solution that worked for me.
[]("http://tinyurl.com/2wv7jd")

---

### Post by miznatt on 2007-04-26
Thank you everyone, got it back up and running :)

---

