---
title: "Transferring firefox bookmarks"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by brodiesel on 2008-03-20
hey everyone, total noob here. 

i just started trying out gutsy last night, and i like it, however the one annoyance that i have is that i've been customizing my xp version of firefox for about two years. for instance, on the bookmarks toolbar i have about forty favicons with the titles erased so i can just hit a button to go to the url.

so my dumb question is, is there anyway to transfer my bookmarks? the only thought i have had so far is trying to use google to index them, but i dont even know if that would work?

any magic solutions?

---

### Post by alex_anthony on 2008-03-20
you can copy the entire profile over. 
its at C:/Documents & Settings/<WindowsUser>/Application Data/Mozilla/Firefox/Profiles/ its a wierd folder name with .default
copy this to /home/<UbuntuUser>/.mozilla/firefox/ 
and then change profiles.ini (in that folder) to have the different profile name as the one you just copied. That copies bookmarks, addons etc, even keeps the right order

---

### Post by danillo on 2008-03-20
To only backup the bookmarks: Bookmarks > Organize Bookmarks > File >Export

---

### Post by brodiesel on 2008-03-20
> **alex_anthony said:**
> you can copy the entire profile over. 
its at C:/Documents & Settings/<WindowsUser>/Application Data/Mozilla/Firefox/Profiles/ its a wierd folder name with .default
copy this to /home/<UbuntuUser>/.mozilla/firefox/ 
and then change profiles.ini (in that folder) to have the different profile name as the one you just copied. That copies bookmarks, addons etc, even keeps the right order


okay, soo... 

since you obviously are way ahead of me on this, let me ask you another goofy questtion: how do i copy this over to ubuntu? flash drive? i'm still really unclear on how to switch things between the two OS's.

---

