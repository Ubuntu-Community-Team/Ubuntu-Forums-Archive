---
title: "problem recognizing cd's in samsung cd-rom drive"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-07-31
whenever i put in a new cd into my cd drive it is not recognized unless i restart ubuntu
when i was installing ubuntu it didn't recognize my cd-rom drive so i restarted the installation and then it did
what can i do to get my cd's to be recognized upon putting them in?
is there drivers i can download? or what?

---

### Post by buixuanduong1983 on 2007-08-01
I have the same problem: when I just install Ubuntu, my CD drive recognize my CDROM when I put it in, but now after a while installing many software, it does not automaticly recognize it anymore, I have to mount it manually:

sudo mount /dev/cdrom /media/cdrom0

then unmount:

sudo umount /media/cdrom0

anyone have resolution for this problem (GnomeBaker still run OK even Ubuntu does not recognize CDROM, but Brasero does not)


to onearmedpanda: if it happend even when you are installing Ubuntu, I think the problem is your CDROM: scratch, dirty... or CD drive eye bad...

---

