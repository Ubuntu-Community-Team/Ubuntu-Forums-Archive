---
title: "system stats"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by defenestratos on 2007-07-07
Where can I get all of my system info (for instance ram and video card etc) in a nice, concise way?
I'm still learning Ubuntu.

---

### Post by macogw on 2007-07-07
Applications > Accessories > Terminal
> sudo lshw
leaving off the "sudo" will give you a less-detailed view (if you don't care to see what firmware version your motherboard has, for example, don't bother with sudo)

That shows memory and everything in what I think is a more human-readable form than System > Preferences > Hardware Information..which I don't think shows memory and really seems to just have a lot of things that no one who's not a system-level programmer would understand.

---

### Post by RomeReactor on 2007-07-07
Hi. I can't quite remember where in Dapper this application is, but I think it's in "System->Administration"; "Hardware" something? You can also try from the terminal (Applications->Accessories->Terminal):
```
sudo lshw
```
Sorry for the vague attempt. ;)

EDIT: D'oh! **macogw** strikes again! :D

---

### Post by defenestratos on 2007-07-07
Thanks perfect.

---

### Post by stefe on 2007-07-08
also do a search on synaptic: hardare information, there are at least 5 different programs.

lshw also has a gui --> lshw-gtk

Enjoy!

---

