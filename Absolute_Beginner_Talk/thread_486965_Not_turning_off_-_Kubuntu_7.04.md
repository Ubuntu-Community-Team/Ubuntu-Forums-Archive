---
title: "Not turning off - Kubuntu 7.04"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by candtalan on 2007-06-28
I installed Kubuntu for a friend - onto a new Dell Dimension (Intel chips). The only problem is that sometimes it does not shutdown properly. On these occasions it gets as far as the Kubuntu (shutdown) splash screen and seems to try and then retry again a few times to shutdown but does not. 

ctrl alt F1 does not get any response and a power force off by holding the button down works, and there are no apparent after effects such as journal lists.

However it is troubling for my friend who (so far) has seen XP working well. Grrr.

Also just before a bad shutdown, on two occasions the screen shows random multicolour effects as if something weird happens to the video area - not sure if this is easily repeatable though. Although it sure frightened my friend.

I would certainly appreciate any pointers to sort this out. 
tia

---

### Post by confused57 on 2007-06-28
> **candtalan said:**
> I installed Kubuntu for a friend - onto a new Dell Dimension (Intel chips). The only problem is that sometimes it does not shutdown properly. On these occasions it gets as far as the Kubuntu (shutdown) splash screen and seems to try and then retry again a few times to shutdown but does not. 

ctrl alt F1 does not get any response and a power force off by holding the button down works, and there are no apparent after effects such as journal lists.

However it is troubling for my friend who (so far) has seen XP working well. Grrr.

Also just before a bad shutdown, on two occasions the screen shows random multicolour effects as if something weird happens to the video area - not sure if this is easily repeatable though. Although it sure frightened my friend.

I would certainly appreciate any pointers to sort this out. 
tia
Maybe this will work:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)
except with Kubuntu, use kwrite instead of gedit...

---

### Post by candtalan on 2007-06-29
Thanks but I do not seem to have /etc/modules in kubuntu 7.04

---

### Post by darkrose on 2007-06-29
so create it.

kdesu kate /etc/modules

put in it what you need and save.

---

### Post by HotShotDJ on 2007-06-29
I had the same symptoms you describe with Kubuntu -- the following link sorted it for me:
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/34821/comments/27]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/34821/comments/27")

---

