---
title: "Ability to mount windows network folders?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by TheShadow99 on 2007-02-21
I'm trying to setup a few Ubuntu systems to test them in my school network (which I'm the admin of). The idea is that I can eventually ween the most problematic users off of windows and onto Linux. It also allows me to teach the kids something about OSS/Linux so things aren't so windows focused in their education.

After solving the first hurdle (failed grub setup on a dual boot machine), I've run into another issue. Certain files are stored on what is currently a windows 2k3 server that people will need access to (rather hard to do timesheets digitally if they can't access the timesheets). Ubuntu sees the domain they are on, but it can't access it.

Any easy solutions?

---

### Post by TheShadow99 on 2007-02-21
Huh... Well after installing a bunch of applications and libraries for connecting to windows resources of various types the problem has fixed itself... I do however wish I knew what pieces actually did it...

I used to networking windows machines, but you don't generally think of a shared resource in windows as the technology sharing it...

edit: 
Ok, now that I can see the rest of the network... Can I make use of that with applications such as wine?

---

### Post by dodgeygeezer on 2007-02-21
just playing with ubuntu for first time to. seems you can put in the location window:-

smb://windowspc/share

to access them, but you have to authenticate each time. not sure how to map it permenantly..

anyone?

---

