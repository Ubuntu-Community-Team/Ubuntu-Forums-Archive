---
title: "adding dvd to rep"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-25
i have a breezy dvd.
is it advisable to add that to repos?
somehow i cant connect to automatix or othere non free sites

when i try to add cd in repo gui it says no cd found.
i have this dvd writer installed recently.
when i put ina dvd on it it does play.

tv

---

### Post by SkyNet2029 on 2006-06-25
You can use
```
#sudo apt-cdrom
```
to add cd's to your repo list. Although it's kind of redundant in application, especially if you are running
Dapper. It doesn't say which, so I dunno. As for connecting to the NON-Free sites, you have to add those to your repos list to connect to them. From personal experience, the Automatix server is up/down rather regularly. I'd post it here, but it's non-free, etc.etc.I personally don't think its
all that advisable to add an cd that contains OLDER source
code than what is default for your current running OS, as in theory alone,
it would possibly attempt to *downgrade*
your apps and toss you into a self-made dependency hell.
If you feel its a must though, kick open a Terminal/Konsole 
and do yourself a favor by going through the Manual.
```
man apt-cdrom
```. And no, I don't mean to say
'RTFM', cause that wouldn't be cool. I mean that there are 
quite a few commands listed there that you might miss
if you just type in 
```
#apt-cdrom --help
```

---

### Post by drtvasudevan on 2006-06-25
looks like the dvdrom is not in the fstab and so it does not show.
became wiser reading all those men (man s)
i will fix it later.
thanks 
tv

---

