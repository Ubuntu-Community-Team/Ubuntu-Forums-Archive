---
title: "Recover Firefox Bookmarks from lost system"
date: 2011-12-24
forum: Any Other OS
---

### Post by silveringking on 2011-12-24
Hello here is the problem I had with some urgency backup all my system (linux mint 11) in order to not lost my files. I did an image with clonezilla, and then I extracted it on a external disk just for the propose of recovering my files. I would like to recover also the bookmarks from my firefox. But I don't know how I can do it. Thank you so much.

Ps: If necessary I still have the clonezilla's images.

---

### Post by gareththered on 2011-12-24
A Google for 'linux firefox bookmarks location' brought up some answers.

The first of those says that Firefox stores these in profiles which are in '~/.mozilla/firefox'.  Within this dir you will find another directory with a strange name.  I believe if you copy the contents of this folder to the corresponding folder on your new machine that all Firefox settings will be available for you.  Note that the folder on the new machine will have a different, but equally strange, name.

For example, mine was called '~/.mozilla/firefox/kwbv5604.default'

---

### Post by silveringking on 2011-12-24
Sorry and thank you!

---

### Post by lovinglinux on 2011-12-24
Firefox bookmarks are located in the ***places.sqlite*** database file, under **~/.mozilla/firefox/xxxx.default/** or something like that. Depends on the name of your profile. You can actually copy the entire **~/.mozilla** folder, so all your profiles, with bookmarks, passwords, extensions, themes and so on will be restored.

---

### Post by mips on 2011-12-25
> **silveringking said:**
> I did an image with clonezilla, and then I extracted it on a external disk just for the propose of recovering my files.

By the way, you don't have to write the image back to a hard drive to access it, you should be able to mount the disk image like you do a cd/dvd and simply copy across what you need. Save you a lot of time and makes life easier ;)

---

### Post by bpb101 on 2011-12-26
use the sync feature , if you have it set it up on lost system
if you haven't got the system you can revover with email and password

---

