---
title: "CD ROM drive not recognized"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by bac2nowere on 2007-06-12
I am new to ubuntu. I have an older computer that use to have ME on it. So, after this computer crashed I installed 7.04. I have it installed now up and running, however, it is slow, could be from having an older processor perhaps. Also, this system doesn't recognize my CD ROMS. It recognizes the 3.5 floppy.
My question is, is there another operating system that would work better or is there something else I need to do. Any guidance would be greatly appreciated

---

### Post by starcraft.man on 2007-06-12
> **bac2nowere said:**
> I am new to ubuntu. I have an older computer that use to have ME on it. So, after this computer crashed I installed 7.04. I have it installed now up and running, however, it is slow, could be from having an older processor perhaps. Also, this system doesn't recognize my CD ROMS. It recognizes the 3.5 floppy.
My question is, is there another operating system that would work better or is there something else I need to do. Any guidance would be greatly appreciated

Ok, first off my sympathies for having used ME for so long. That may just be the single worst edition MS has ever made (may just beat out Vista, we'll see).

Can you give us a complete hardware list: Mobo, CPU, Ram, Graphics Sound card, Optical Drives, etc... That will help for starters.

If your running on an old P3 with not too much ram, yes Ubuntu may be slow or rather GNOME would appear slow. GNOME is just one of many front ends you can use. For older systems you'd want to look at xfce. Maybe even getting a new comp...

As for the Drive issue, I dunno. Seems weird. Drives usually run just fine, maybe it has to do with yours specifically. You do know they don't appear in the desktop/places section unless there is media in them right? Linux only mounts them when they have something, Windows keeps them mounted always.

---

### Post by arvevans on 2007-06-12
Is your CD-ROM drive an ATAPI interfaced device (most are)?  When you go into the CMOS setup pages, does it indicate that you have a CD drive?  If no, the CD-ROM drive may be faulty.  How did you install Linux without the CD-ROM drive?  If you used the CD drive for installation, then the CD-ROM device will probably work with Linux.  Look in /etc/fstab to see if it is mounted...if not, mount it.  On a terminal screen do "man fstab" and "man mount" to see how to do this.

DISCLAIMER:
[LIST]
[*]Hardware that will not run Windows will probably not run Linux.
[*]Installing Linux on a broken computer will not fix it.
[*]Computers that run slowly on Windows will probably also run slowly on Linux.
[/LIST]

---

### Post by starcraft.man on 2007-06-12
Just a note but arvevans you should really get a mod to change your name, spammers troll these forums regularly and your likely to get flooded by mail you don't want.

---

### Post by arvevans on 2007-06-12
What makes you think that is "my" email address?
_._

---

