---
title: "questions about dual boot options"
date: 2007-03-31
forum: Apple PPC Users
---

### Post by Nefarious on 2007-03-31
Well I have in my possesion an apple quicksilver 933mhz 1.5gb ram, running os x and I would like to keep it that way. what I dont have is an os x install disk as I got my mac with it, so it is important that I dont screw things up to badly. What I want to do is use another hard disk that I have to install ubuntu and leave the other disk alone, but Im not sure that the computer is going allow booting from that drive or not. Also, is install on ppc the same as on normal pc's (with a gui) or is it through a command promp?

---

### Post by ZoiaGuyver on 2007-04-01
It should be fine installed on another drive. 

Im not 100% sure but i think on most the macs holding the "option" key at boot allowed you to choose the boot drive, bypassing the others. The only problem i could see you having was Yaboot as that does like to be in control of everything (much like the standard mac loader :P), but i should think a little reading up on it should sort it.

Hope this helps a bit i dont really know what else to suggest. I personally havnt dual booted my mac in a long time (straight linux installs on all of them apart from 1 that i got a few days ago :P)

---

### Post by grazie on 2007-04-01
You'll have no problems using a second disk. If you wanted to be absolutely certain of not messing up your OSX disk you could disconnect it while installing linux on the other hard drive, but that would be super cautious. You'd have add OSX to yaboot yourself after installing linux though, but it is easy enough.

You could use the Desktop or Alternate CDs to install from. Desktop uses gui based installer and Alternate uses text/graphical installer. The Desktop CD has the advantage of being able to live boot and is better for recoveries if necessary at a later date in my opinion. The Alternate is aimed at low ram machines and seems to be more reliable (on x86 machines at least).

A second hard disk is not essential as you could use something like gparted (Desktop CD only) to resize  and create new disk partitions, but without a means of OSX and data recovery that would be very risky.

---

### Post by Nefarious on 2007-04-12
Thanks sorry it took so long (Im on spring break). Ill have to buy another harddrive know that I used the one I had for backing up stuff :roll:

---

