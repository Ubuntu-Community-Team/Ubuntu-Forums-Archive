---
title: "partition and read file problems- please explain with small words!"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by karinne on 2006-11-07
Hi all, 
I successfully installed ubuntu, and enjoy the GUI and am learning (slowly) my way around a CLI- last time I used one was a LONG time ago, unless you count AutoCAD, where the CLI is easier to use than the mouse. 
I suspect eventually that here in ubuntu, the CLI will also become easier, but currently i'm LOST. 
here's problems 1 and 2. 
1) I would like a way to view (at least, if not edit) the documents etc. on my windows partition. 
2) when installing ubuntu, I accidentally made my ubuntu partition the larger of the two. I do a LOT of 3D solid modeling and editing big files running in XP, so I had intended THAT partition to be the larger of the two. 
How, pray tell, do I resize them? 

Please- if you don't mind, use simple step by step directions. I am still learning commands, what they mean, etc. 
thank you!
regards
karinne

---

### Post by po0f on 2006-11-07
karinne,

I can't comment on how to resize the partitions as I've never had to do that, but I wouls *highly* suggest booting Windows and backing up all those important files before you do *anything* anyone later will suggest.

---

### Post by bulldog on 2006-11-07
The best way is to download the Gparted ISO [aprox. 25MB] and burn it to cd.
Boot from it and resize the partitions you wish.

Before you resize it's a good thing to defragment your windows partition several times.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

When you boot from cd it's self explaining,take a look and if you don't know what to do,post back.

Succes.

---

### Post by karinne on 2006-11-07
Newest release of GParted? There's a truckload of them. I am assuming so, and going to get it now. Thanks, I'll be back.
-karinne

---

### Post by karinne on 2006-11-07
does the cd/dvd creator - file browser work in 'create data disc' for burning an iso, or should i go look for cd burning apps in Synaptic? 
thanks

---

### Post by bulldog on 2006-11-07
I prefer k3b as burning program.
```
sudo aptitude install k3b
```should do it.

---

### Post by karinne on 2006-11-07
146 MB installed? (says it needed 48 MB of archives.) That's a pretty damn big application. For a CD burner? it seems to be installing a bunch of k-stuff- i'm on Ubuntu not Kubuntu. hmmm. I'm wondering if this was a good idea.
now it's "setting up k-desktop'. This is not what I want, I believe.
But now that it's in my apps list, I'll try it out. hmmm- there's a selection for 'burn iso-dvd, burn data-cd, no burn iso-cd. 
I'm giving it a try, though. luckily, i have a new 50-stack of cheap CD's. 
thanks-
karinne

---

### Post by bulldog on 2006-11-07
K3b is the default burning app. for Kubuntu but works great in Gnome too.

It's easier to use as gnomebaker that's why I proposed it.

But if you think you want to get rid of it just type in your terminal```
sudo aptitude remove k3b
``` and all of it will be removed.

Be sure to use aptitude and not apt-get though.

---

### Post by karinne on 2006-11-07
nah, letting it ride for now. I may check out KDE later anyway. I have a f**ing HUGE hdd at the moment- feeling like i'll "never" fill it up (300GB), but I know eventually that will change- 4 years ago I thought that about 50GB!
leaving ub-land, going back to win to defrag, back here to run Gparted. (assuming it's set up to run under ubuntu not windows.)
thanks again, 
k

---

### Post by Bartender on 2006-11-07
GParted runs as a bootable CD, so it doesn't run "under" either OS.

---

