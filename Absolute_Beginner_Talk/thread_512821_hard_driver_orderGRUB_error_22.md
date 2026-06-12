---
title: "hard driver order/GRUB error 22"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Trebaruna on 2007-07-29
I've a very annoying problem, it seems to be Linux-at-large related, not just Ubuntu.
Since I included a fifth hard drive in my computer I've had to spread my drives over the two SATA controllers on my board: my system drives (2 of them) are now on the nForce 4 controller, the data drives (3 of those) are on the onboard Sil3114 controller. So far so good.

Windows has no problem in seeing or accessing the drives: it puts them in order nicely, always the same order, and doesnt do anything silly.

Linux, however (Ubuntu and the Fedora 7 GNOME LiveCD) jumble the drives around all the time. One boot the one controller is on top, the other boot the other.

Of course, this makes installation very difficult, if not impossible. When I boot it and the drives appear as I want them to (and windows sees them, and the BIOS recognizes them: nforce first, then the sil3114) I go about installing, but when I reboot GRUB throws an error 22 at me.

By now I am at a loss. I have no idea why Linux is being so indecisive about these drives, and I have nowhere near enough knowledge to figure out where it decides and how I can make it decide the same way all the time.

If anyone knows what I might do, I am listening. Right now I am very frustrated: Ubuntu has given me a very smooth ride up to this point (before I had to use the second controller), but now it seems there's a showstopping problem, and I have no idea whatsoever how to fix it... :(

---

### Post by ddrichardson on 2007-07-31
Sorry I can't be more helpful - but this issue with grub and multiple controllers is known (and infact there is a [blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/grub-disk-map-sanity") for it with gutsy) but progress has been slow.

AFAIK, Windows allocates drive numbers in relation to their BIOS codes. Unfortunately I don't think using NTLDR in Windows to boot ubuntu will work either because it will hand over to grub which will probably still mess up the drive order.

Its listed as a blueprint for gutsy though so you never know progress may be made.

---

