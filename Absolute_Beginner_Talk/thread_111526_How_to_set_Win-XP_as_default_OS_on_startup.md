---
title: "How to set Win-XP as default O/S on startup ?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2006-01-02
I have just installed the latest Ubunto Linux. I'm currently configuring it to add tools and software.

I'm kinda new to Linux but not to Unix.

One thing I noticed upon booting, on the multiple O/S pannel, where you select which O/S you want to boot, my Win-XP isn't the default one. 

How can I change it ?

I have users on my PC that must have XP boot by default.

---

### Post by jrib on 2006-01-02
Change the "default" setting in /boot/grub/menu.lst to the appropriate number.

When you see the menu just count on which line Windows XP shows up (note that section titles count as a number and numbering begins at 0)

So if you have something like:

Ubuntu
Ubuntu recovery
Ubuntu Memory test
Other OS's:
Windows Xp

you would set default to 4

---

### Post by Browser_ice on 2006-01-02
That file to change is residing where ?   
- On my Linux partition
- On my Xp partition
- on a boot sector ? if so, how can I change it

---

### Post by dueY on 2006-01-02
[QUOTE=Browser_ice]That file to change is residing where ?   
- On my Linux partition
- On my Xp partition
- on a boot sector ? if so, how can I change it[/QUOTE]

/boot/grub/menu.lst   -  on the Linux partition
and you type 
sudo gedit /boot/grub/menu.lst 
to edit it

---

### Post by kingsidy on 2006-01-02
this is how i change the menu. fire up the terminal type in > sudo gedit /boot/grub/menu.lst it will ask for your password, then it will open the text editor. Scroll towards the bottom of the page, then you'll see the list that appears when u boot. you'll see like linux kernerl 2.6.12.10 i386 and stuff like, if you look closer at the bottom you'll see a line that says other operating system and you'll see windows xp listed under there. Copy the whole windows xp section and paste it at the beginning of the list right before the first linux kernel image 2.6.12.10. then save. when you reboot, xp would be at the top of the list therefore becoming the default OS it boots to. basically you just rearrange the order of the items in the list.

---

### Post by Browser_ice on 2006-01-02
I chose the default num instead. I updated it and saved it.

(I'm typing this via Firefox in Linux, cool !).

I'll reboot and see.

If you don't hear from , then its ok.

Thx guys !

---

