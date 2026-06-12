---
title: "ah! gdm help please!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-10
When I booted up my computer it sent me to basically to a black and white terminal that covers the whole screen (unable to see desktop or anything). But prior to that it states "The GDM group 'gdm' does not exist. Please correct GDM configuration and restart again." My only option from there is to hit okay. And move along to this black and white terminal. What do I do?! Please help asap.

---

### Post by ukulele_ninja on 2007-08-10
Im hardly an expert, but at startup it should give you the option to start in GDM or to choose a different manner from a drop down box. Try choosing 'default' from the drop down box and see if that solves it.

---

### Post by jolan_jj on 2007-08-10
you can try to type ```
sudo apt-get install --reinstall gdm
```, it should help.

---

### Post by CapitanYochua on 2007-08-10
Before I read that last post. I tried sudo apt-get remove gdm. Then sudo apt-get install gdm.
That worked for me. But now I have a new error. One with HAL. So I think I'm going to post a new thread for this new error.

---

