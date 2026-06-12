---
title: "Disk Utility equivelant for Ubuntu?"
date: 2006-10-01
forum: Apple PPC Users
---

### Post by meshica7 on 2006-10-01
I am running Ubuntu 6.06 on a Power Mac G4.Is there any way of running a systems check from the command line? I used to do this in OS X with the Disc Utility app and by typing **FSCK -Y** when booting into the command line (Darwin) on my Mac to run a file check.Is there a comparable command or perhaps an app like Norton Utilities or MacAffee that will do a /defrag/disk/file check in Ubuntu?I would prefer an app as I am a command line amatuer,but I am willing to learn!;) 
Thanx!

Juan

---

### Post by kidders on 2006-10-01
Darwin is effectively BSD, which is very closely related to Linux (Ssshh... don't say that too loud!) the **fsck** utilities are available on both systems and work very similarly.

Any graphical utilities you might find will most likely just be front-ends for fsck ... just like the OS X disk checker is.

---

### Post by meshica7 on 2006-10-06
Kidders,
Thanx for that bit of info! 
 Would it be best to run this at start up or from a console within Gnome/KDE?
Thanx!:mrgreen: 
 Juan

---

### Post by kidders on 2006-10-06
Hey again,

Your system probably already does a basic fsck at startup.

If you happen to want to do a manual disk check, you should bear in mind that, like in OS X, you won't be able to do much actual *repairing* while your filesystems are mounted.

Where you run fsck from really doesn't make much difference though :-)

---

