---
title: "add/remove won't open"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-22
I'm trying to install a program so i can delete the partition on my other drive and format it, but i click the add/remove thing, it loads the hole bar and then it closes...  what happening... how do i fix it... thanks

---

### Post by bulldog on 2006-09-22
Try synaptic or the terminal

sudo aptitude install name of your app.

---

### Post by Devile on 2006-09-22
ok then what is a good app for what i need to do?

---

### Post by aysiu on 2006-09-22
Using *aptitude* will help you diagnose what the problem is.

Let's say you're trying to install Konqueror. Paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install konqueror
``` Do you get any errors?

---

### Post by bulldog on 2006-09-23
> **Devile said:**
> ok then what is a good app for what i need to do?

Well if you want to format or resize your other hdd,try gparted,it's working fine to me.

sudo aptitude install gparted

A little warning,be very carefull and look twice if the settings you want are good,before you apply.

And the disk you want to manage must be unmounted before you can alter.

---

