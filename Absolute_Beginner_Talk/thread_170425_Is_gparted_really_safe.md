---
title: "Is gparted really safe?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by nickle on 2006-05-04
I would like to change split my home partition and am wondering if gparted is really reiable?. My home partition is on a RAID 1 split over two disks and I keep a regular backup copy of home  tree on a seperate disk.


Can anybody give some advice on how best to do this?

---

### Post by steve.horsley on 2006-05-04
I have an outstanding bug report on the parted library, but it was an old version. Gparted do their own live CD which has a later version. I'd look up my mails on the bug for you, but incredibly, gmail is down at the moment - I get 404 errors.

I have seen suggestions to use diskdrake from a Mandriva installer CD (or live CD I suppose). I would be inclined to trust that more, having seen gparted mangle my own partition table.

I've never used raid at all.

---

### Post by ncappel1 on 2006-05-04
as I understand it, Gparted is really just like a graphical front end to fdisk. It is definetely reliable, i've used it a bit before, I can't say that the user at the controls is 100% reliable though! ;) hehehe

a cool feature of Gparted is that before any changes are written to the disk it shows you a summary of what is going on, that way you can see **exactly** what you are planning to do. It also won't let you do things that shouldn't happen, like say, deleteing an active swap partition.

---

