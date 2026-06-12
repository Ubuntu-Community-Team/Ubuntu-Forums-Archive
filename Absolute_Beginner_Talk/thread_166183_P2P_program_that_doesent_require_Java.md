---
title: "P2P program that doesent require Java"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by RobyX on 2006-04-25
OK I think i've basicly given up on installing Java for linux.. been trying since I came back from school..

So since I can't use Frostwire, is there any program that will let me install anything like Frostwire with no Java?

---

### Post by Nikusan on 2006-04-25
[QUOTE=RobyX]OK I think i've basicly given up on installing Java for linux.. been trying since I came back from school..

So since I can't use Frostwire, is there any program that will let me install anything like Frostwire with no Java?[/QUOTE]

Try gtk-gnutella:
```
sudo apt-get install gtk-gnutella
```

Were you trying with the sun java or one of the free versions? It's quite easy to install sun java if you follow the instructions on the [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca") wiki page.

---

### Post by jazzmuzik on 2006-04-25
Amule is a bit like Frostwire.

bittornado isn't like Frostwire but it doesn't use java.

---

### Post by auroraborealis on 2006-04-25
nicotine is a linux version of SoulSeek (music only).

---

### Post by TuskenR on 2006-04-26
In my opinion the best is  **rufus**.

---

### Post by mjm115 on 2006-04-26
I use amule and apollon.  gtk-gnutella is also good.

---

### Post by Bloch on 2006-04-26
gtk-gnutella has a geeky interface but it works well for me. Frostwire damands 300+ MB - it seems to be a kind of bug, but if you have 512MB then it will work fine.

This is one case where you should install the latest version as it has the latest list of servers. The one got using synaptic is not broken, it's just that its built-in list of servers is old and it might fail to connect.

Do a google search for
GTK1_gtk-gnutella_0.96.1-0_i386.deb
or else go straight to the gtk-gnutella homepage. Download the file above and place it in your home directoty. Open a terminal. Install using
dpkg -i ******.deb
where *****.deb is to be replaced with the package name - most like;y the one above unless they brought a new one out in the last few hours!!
It will be on your menu

---

