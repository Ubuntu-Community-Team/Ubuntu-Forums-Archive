---
title: "NTFS resize..."
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by Narpas on 2006-04-02
Good idea or not:

To resize an NTFS drive, I plan to use gparted with ntfsprogs. The resize function seems very simple, and the team behind ntfsprogs seems very confident in its ability. I'm willing to use DiskDrake, but as this looks like it should work, I think I might not have to.

Also, what's the best program to defrag the NTFS drive? Or does ntfsprogs do that automaticly?

---

### Post by dcstar on 2006-04-02
[QUOTE=Narpas]Good idea or not:

To resize an NTFS drive, I plan to use gparted with ntfsprogs. The resize function seems very simple, and the team behind ntfsprogs seems very confident in its ability. I'm willing to use DiskDrake, but as this looks like it should work, I think I might not have to.

Also, what's the best program to defrag the NTFS drive? Or does ntfsprogs do that automaticly?[/QUOTE]
I used a Linux based tools CD and qtparted to resize a NTFS partition a few weeks ago with no issues.

---

### Post by siminone on 2006-04-02
I did the same myself but I defraged my NTFS partition from WinXp.

 It's better to be safe than sorry :p

---

### Post by plors on 2006-04-02
[QUOTE=Narpas]Good idea or not:

To resize an NTFS drive, I plan to use gparted with ntfsprogs. The resize function seems very simple, and the team behind ntfsprogs seems very confident in its ability. I'm willing to use DiskDrake, but as this looks like it should work, I think I might not have to.

Also, what's the best program to defrag the NTFS drive? Or does ntfsprogs do that automaticly?[/QUOTE]
its save if you use the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). You don't have to defrag your filesystem first, ntfsresize (which gparted uses) will do this for you.

Although this is considered to be safe, it's always a good idea to make a backup of valuable data!

---

