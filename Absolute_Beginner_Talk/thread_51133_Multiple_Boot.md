---
title: "Multiple Boot"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-07-22
Hey Guys,

I was thinking about getting linux, and I found out unbuntu was free, and It all seemed easy enough,

So I have a few questions

1. Is it possible it install it with another operating system (Windows XP Home)

2. If it is possible will I get a menu on boot of wether I want Windows or Linux?

3. It is any good for a personal home PC

---

### Post by varunus on 2005-07-22
1 and 2: Ubuntu has the capability to install alongside Windows.  It will present you with a menu every time you turn on the computer of which OS you want to load.

You have to repartition your hard drive to do this, but its not that bad...Ubuntu will do most of the work.  Here's a guide on how to repartition your hard drive in the Ubuntu installer (with pictures!): [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

3:  Ubuntu works wonderfully for a home PC.  That's what I'm using mine for.

---

### Post by lavarock09 on 2005-07-22
Is a repartition where it makes the hard drive and PC think there is two hard drives so you can use 2 OS's, and would the Unbuntu disk do all that for you or would you have to do something manually

Sorry, but I occasionally get problems where sites don't load and that is one of them

---

### Post by varunus on 2005-07-22
The site won't load?  That's not that cool...Its a very useful site, has pictures of how to repartition.  What browser are you trying to load it in?

Yes, repartitioning is where you split your hard drive into two, so you can install one operating system on each.  The ubuntu installer can do the repartioning for you; the link above is just how to use the installer to do so.

You have to manually choose to repartition in the installer; when it comes to the partition step, choose manual;  you then need to select your windows partition (which will be listed) and reduce the size.  Then, you can select the "free space" and choose "automatically partition" on it.  Ubuntu will then install happily alongside windows and install its boot menu (GRUB).  (When it asks about GRUB, choose to install it to the "master boot record" so the menu will come up when you boot.)

---

### Post by lavarock09 on 2005-07-22
[QUOTE=varunus] and reduce the size.[/QUOTE]

Reduce The size of what?

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=lavarock09]Reduce The size of what?[/QUOTE]

Of your Windows Partition. The big NTFS c drive. Linux needs its own partition like Windows does.

---

