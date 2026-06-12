---
title: "not able to autorun any disks...is this normal?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Nyxess on 2007-06-27
it seems i cant autorun any cds, or at least not the three that ive tried. is this because they were made for windows? and if so how can i create a cd on other computers with the ability to autorun in ubuntu?

---

### Post by Pragmatist on 2007-06-27
What do you mean by "autorun"?  Do you mean "automount"?  In Windows, you can put a disk in, and it will automatically start a particular program--i.e. if it is some kind of install disk, a wizard will start.  This is called "autorun" as a program is automatically run (started).  In Ubuntu, "automount" means that when you insert a disc, it is automatically available for access--you can view its contents.

Some people want to automatically "run" a file manager like Nautilus when they insert a disc.

What are your trying to do exactly?

---

### Post by Inxsible on 2007-06-27
Go to System-> Preferences -> Removable Drives & Media (i think:-k )
 
In there you can select the default applications that you want to use for particular kinds of discs. Like I have rhythmbox setup as my Audio CD player, so it starts up the moment i put in a Audio CD. Totem setup as my DVD player...and so on.
 
All other data CD's open up nautilus for me.
 
HTH.

---

### Post by ectospasm on 2007-06-28
I've got this same issue, and I've made sure "Play audio CD discs when inserted" is checked (my program is grip, so I don't necessarily want to play it, but that should be immaterial).  

I finally fixed it, but it required a reboot.  Simply logging out and logging back in didn't work when it should have.  YMMV.

---

### Post by alienexplorers on 2007-06-28
Is your CD/DVD listed in your fstab:
> /dev/hdc        /directory/name   udf,iso9660 user,noauto     0       0

---

### Post by Nyxess on 2007-06-28
i think i figued it out. what i was trying to do was install World of Warcraft(which isnt going to work at all without Wine i guess). thanks for the help =)

---

