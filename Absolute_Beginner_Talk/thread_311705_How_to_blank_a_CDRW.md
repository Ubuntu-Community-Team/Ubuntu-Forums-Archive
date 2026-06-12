---
title: "How to blank a CD/RW"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by xeo_pt on 2006-12-03
Using this [tutorial]("https://help.ubuntu.com/community/CdDvdBurning") I can burn CD/RW but how do I blank them to re-use?
The tip in the end of the tutorial doesn't work.

Regards.

---

### Post by lamego on 2006-12-03
If you would like to do it from the GUI you can install Brasero:
[http://www.getdeb.net/app.php?name=brasero](http://www.getdeb.net/app.php?name=brasero)

---

### Post by d3v1ant_0n3 on 2006-12-03
KDE's cd burning prog, k3b (works on gnome, is in the repos, is wonderful IMO) will blank cd-rw's before writing to them, complete with prompting so you don't kill anything important.

---

### Post by xpod on 2006-12-03
GnomeBaker does it simply too i although i`ve only ever burned stuff with it and have never had need to wipe any rw`s yet.

---

### Post by pistcivet on 2006-12-03
I've had some bad experiences when using cdrecord,
a similar (and more reliable) tool is cdrdao.

You'll probably have to fire up Synaptic to install it,
then do a "man cdrdao" to learn how to use it.

Using cdrdao to blank a CD-RW is very easy (no TOC file is needed when blanking).

---

### Post by msak007 on 2006-12-03
I'll second d3v1ant_0n3's vote for K3B. You can either blank CDRWs manually or, like he said, set the option to automatically erase when you burn to it again. I do it all the time when creating MP3 discs for use in my car and it works great. Depends on whether you want to do it using the terminal or a GUI.

---

### Post by xeo_pt on 2006-12-03
Thank you to all of you guys.
I follow d3v1ant_0n3  advice and I'm using k3b, and it's great.

Thank a lot.

---

### Post by Shay Stephens on 2006-12-03
k3b is the best burner out there right now, even if you are running gnome.  It lets you verify data, which gnomebaker can't do, and there is no indication it will in the near future either.  k3b is more stable than nerolinux too.  After trying everything out, I keep going back to k3b.

---

