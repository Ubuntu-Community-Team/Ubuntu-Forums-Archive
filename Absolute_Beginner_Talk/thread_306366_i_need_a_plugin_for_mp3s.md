---
title: "i need a plugin for mp3s"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2006-11-24
where could i get a plugin?

note, i cannot download directly from linux, its on a computer unaccessable to the  internet atm.  i've been transfering via my Ipod.

---

### Post by tubasoldier on 2006-11-24
Plugin for what exactly? to play mp3 files?

---

### Post by rlozano on 2006-11-24
> **meteora184 said:**
> where could i get a plugin?

note, i cannot download directly from linux, its on a computer unaccessable to the  internet atm.  i've been transfering via my Ipod.

for ease of use, you can try [www.getautomatix.com](www.getautomatix.com) to help you install the codec/plugin you need to play your mp3.

---

### Post by meteora184 on 2006-11-24
that requires internet connection doesn't it?

---

### Post by kinson on 2006-11-24
> **meteora184 said:**
> that requires internet connection doesn't it?

Yes, but almost everything here requires the internet, no? :confused: 

After all, if you're requesting a "plugin", you'll still need to download that right?

Kinson.

---

### Post by rlozano on 2006-11-24
> **meteora184 said:**
> that requires internet connection doesn't it?

yes. actually, i don't think you can get the codecs/plugin you need atm, without internet connection unless you have it already downloaded coz all of them are in a repository accessible via the internet.

---

### Post by CatKiller on 2006-11-24
> **meteora184 said:**
> where could i get a plugin?

note, i cannot download directly from linux, its on a computer unaccessable to the  internet atm.  i've been transfering via my Ipod.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You can access the files that are in the repositories as .debs from packages.ubuntu.com. You'll probably have to sort out the dependencies yourself this way. You might be able to put the .debs  in /var/cache/apt/archives and use Synaptic, but you might need to use **dpkg -i** instead, in which case you'll need to put packages that depend on each other in the same command.

You may find it easier to get Internet access for that computer, at least temporarily. Also, you might find these pages useful to read.
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

