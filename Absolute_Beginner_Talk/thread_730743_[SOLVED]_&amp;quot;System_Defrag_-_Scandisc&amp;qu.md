---
title: "[SOLVED] &amp;quot;System Defrag - Scandisc&amp;quot; in Linux"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-21
I have glitches in my add/remove, synaptics manager and a few other areas - how do i do a system repair like u would in windows. Do not want to have top reinstall - way to much work done to this.

---

### Post by dacorr on 2008-03-21
linux disk structure does not need to be defraged.

If you are having trouble with the package manager could you post the error message it gives you and what you were trying to do when it gave you the error message then i can see if i can help.

Dacorr

---

### Post by DezSP on 2008-03-21
Did you perhaps quit the installer/updater when it was part-way through something? If so, try running (in terminal):

sudo apt-get -f install
sudo apt-get autoremove

Sudo will ask you for your password when you run these. If you do end up needing to do a clean install, make a backup of all the .something files and folders in your home directory, these contain your config files and should make it go a bit smoother. :)

---

### Post by N1N31NCHN41L5 on 2008-03-21
add/remove locked up over a 28 hour period and synaptic manger froze up with the spinning wheel for hours. when they both did this they had come from halfway behind another window and the missing parts of their windows never returned.

---

### Post by N1N31NCHN41L5 on 2008-03-22
If you look up in this thread you will see where i started to remove Alsa well over 15 hours ago and synaptics manager is still hung up on removing it. WTF???? I have come to the conclusion my xubuntu is corrupted. can installing programs from other "flavors" of ubuntu have done this to me?? I am going to reload and see if it fixes it, but how do i avoid ending up right back here again.

---

### Post by mikewhatever on 2008-03-22
> **N1N31NCHN41L5 said:**
> I have glitches in my add/remove, synaptics manager and a few other areas - how do i do a system repair like u would in windows. Do not want to have top reinstall - way to much work done to this.

There is no 'System Restore' function' in Ubuntu, but, perhaps, indicating what the glitches are may get you some help. Also, I am not quite sure why you Defrag is in the thread title.

---

### Post by N1N31NCHN41L5 on 2008-03-22
> **mikewhatever said:**
> There is no 'System Restore' function' in Ubuntu, but, perhaps, indicating what the glitches are may get you some help. Also, I am not quite sure why you Defrag is in the thread title.

i tried to remove gnome alsa about 18 hours ago, and synaptics manager is STILL stuck tryin to remove that one program. I run into the same issue with add/remove.  Can installing programs from other "flavors" of ubuntu have been what caused this problem??

---

