---
title: "I think I broke it!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by wyntermuse on 2007-06-09
So, I have been running Ubuntu, Fiesty on a desktop for a while now. 
In a back handed attempt to try out KDE (I was using gnome) and finding I didn't like it, I opened up synaptic and become overzelous. Now, when I boot  up, I get a text login. I login and it drops me to a prompt like I opened up a term. 

How do I get gnome back?

---

### Post by starcraft.man on 2007-06-09
> **wyntermuse said:**
> So, I have been running Ubuntu, Fiesty on a desktop for a while now. 
In a back handed attempt to try out KDE (I was using gnome) and finding I didn't like it, I opened up synaptic and become overzelous. Now, when I boot  up, I get a text login. I login and it drops me to a prompt like I opened up a term. 

How do I get gnome back?

What do you mean by overzealous? I mean, what exactly did you modify? Just installing the kubuntu-desktop package shouldn't cause any problems, it just becomes an option in the sessions.

Can you elaborate exactly what you modified to get booted to console?

---

### Post by wyntermuse on 2007-06-09
I /thought/ I was removing KDE elements. I did a search for KDE, looked for the green installed boxes and started to un-install. I did a few, rebooted and that's when it went down. I unfortunately don't remember exactly what the last thing on the list was that I removed.

---

### Post by diatribe on 2007-06-09
you really should not do things like that you can break your system easily.  when you get to the propmt login and try typing gdm, if it doesnt work type 
sudo apt-get install gdm ubuntu-desktop
and it should work

---

