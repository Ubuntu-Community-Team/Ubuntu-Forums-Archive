---
title: "keyboard and mouse not working on macbook"
date: 2006-09-23
forum: Apple PPC Users
---

### Post by GhandiBurger on 2006-09-23
I installed Dapper on my MacBook about an hour ago. I installed the 915 resolution package and restarted my computer. Ubuntu booted fine, but when I got to the login screen, the mouse and keyboard would not respond.

I used this to install Ubuntu. [http://www.xs4all.nl/~hajk/mbook-install.pdf]("http://www.xs4all.nl/~hajk/mbook-install.pdf")

Everything worked fine until I installed 915resolution and rebooted

---

### Post by hajk on 2006-09-24
I'm sorry to hear that you ran into problems this way. It's the first time I hear that installing 915resolution doesn't work, and (assuming that you followed all the steps in my notes in the right order) I have no ready explanation for it.

One thing you could do: start the liveCD again, mount the /dev/sda3 Ubuntu partition and review the contents of /var/log/Xorg.0.log for hints on what caused the problem. You could also start the recovery session and do the same thing, possibly followed by removing or reinstalling the 915resolution package.

If all else fails, then you might remove Ubuntu from the HD (I have a note on that as well) and go the Parallels VM route. That's what I did in the end, and I'm very pleased with it.:)

---

### Post by GhandiBurger on 2006-09-24
I think I might have screwed up when I removed the old 386 packages. After I removed all 5, I checked to see if the 686 packages were installed, and they weren't. Maybe that could be it. I plan on doing a new ubuntu install today.

---

