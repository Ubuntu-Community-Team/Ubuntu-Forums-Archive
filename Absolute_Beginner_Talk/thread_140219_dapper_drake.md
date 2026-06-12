---
title: "dapper drake"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-05
when it is released and stable,

how will i upgrade to it?

do i have to fresh install or does the repositories just update/upgrade?

i'm curious the process.

and is there a link to all the new features?

---

### Post by Xian on 2006-03-05
I've done a couple of fresh installs of Dapper, and some upgrades from Breezy (the last one being today). The upgrade process is not yet at a finished state, but even at this Dapper-alpha stage I was able to complete an 'apt-get dist-upgrade' with only a few minor hiccups that were easily fixed during the process. I purposefully set my /home to a separate partition to see how many of my user prefs would remain intact, and everything save for the gnome-session configs were just as I had set them.

By the time of the final release I would expect a very easy transition. The new features are available in the wiki and refreshed with each new released stage.

---

### Post by mavr on 2006-03-05
[QUOTE=Xian] The upgrade process is not yet at a finished state, but even at this Dapper-alpha stage I was able to complete an 'apt-get dist-upgrade' with only a few minor hiccups that were easily fixed during the process. [/QUOTE]

Is it safe to do? Is it any way to undo the process if anything goes wrong?

---

### Post by Xian on 2006-03-07
No, it's not safe. Yes, you can undo it (in theory).

---

### Post by cvcaelen on 2006-03-07
>  I purposefully set my /home to a separate partition

chiming in here with a Q.: could I copy the /home on a flash disk instead?

Christiaan

---

### Post by cotcot on 2006-03-07
Moving home to flash disk should be possible. It is not just moving. Here is a way to do this  : [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by cvcaelen on 2006-03-07
Thanks for that :thumbsup:

Christiaan

---

### Post by mavr on 2006-03-14
Very impressive. Could i create copyes of /opt and /home to an external drive and put them back, overwriting the fresh installed ones? Is pretty much the same thing, but it doesn't force me to have more partitions and i can do it without have the external drive always with me. 

But the real question is: how can this help me going back if a distro-upgrade fail? I don't think that the files on home are the only one to get affected by that. How can i be sure that the process actualy has te possibility to be inverted without errors if something fail in the upgrade?

---

