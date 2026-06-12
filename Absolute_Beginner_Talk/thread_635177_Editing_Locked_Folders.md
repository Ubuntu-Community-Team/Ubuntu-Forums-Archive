---
title: "Editing Locked Folders"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by shortridge11 on 2007-12-08
Hi all
I've looked through a lot of the other posts and i didn't see an answer for my question, so i'll just make a new thread
I wanted to do the theme for Mac, but the way i was doing it ([http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2)) i needed to put files in folders that only the root has access to.  I know i can probably just sudo it through the terminal window, but it would be easier for me if i could make it so i could just edit things in the folders through the gui.  Is it possible to set root privileges for any user you want? or is that impossible?

---

### Post by perce on 2007-12-08
Open a terminal and type 
gksu nautilus

It will open the file browser with root privileges.
I don't know any completely graphical way to do what you want.

---

### Post by spiderbatdad on 2007-12-08
strongly recommend against following those instruction, enabling the repos, and installing beagle...that is all...

---

### Post by shortridge11 on 2007-12-08
what i wanted to do was change the splash screen.  I was using GtweakUI but to put the files in the folder i needed to have access...should i just be using the terminal? and what command would do it for me?

---

### Post by perce on 2007-12-09
> **spiderbatdad said:**
> strongly recommend against following those instruction, enabling the repos, and installing beagle...that is all...

Why? does it do any harm opening a file browser with gksu? I've never actually done it, I've only checked that it's possible.

What does exactly beagle do?

---

### Post by aysiu on 2007-12-09
> **perce said:**
> Open a terminal and type 
gksu nautilus

It will open the file browser with root privileges.
I don't know any completely graphical way to do what you want.
I second the motion. If it's something you plan to do quite often, consider creating a keyboard shortcut or launcher icon for the command ```
gksudo nautilus
``` And, no, there's no reason to recommend against following that instruction. It's perfectly fine. In fact, I don't see how Beagle and enabling extra repositories has *anything* to do with installing a splash screen.

---

### Post by santiagoward2000 on 2007-12-09
I've used **gksudo thunar** (I'm not using Nautilus) a couple of times, and had no problem with it. Unless you delete some critical folder, I would agree with perce and aysiu, it's perfectly safe.

---

