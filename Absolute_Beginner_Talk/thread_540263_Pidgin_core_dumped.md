---
title: "Pidgin core dumped"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2007-09-01
I was tinkering with the auto-away feature when Pidgin suddenly exited itself. I tried launching it again but didn't work. Tried from command line typing "pidgin" and it said Segmentation Fault (Core Dumped). Restarted the system, no luck either (This post is after 1 restart).

Is there anything I can do?

---

### Post by robotii on 2007-09-01
Have you tried updating your system to get the latest version?
If that doesn't work, or there are no updates, do you get a crash report generated?

Finally you can see how to report a bug at [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by finer recliner on 2007-09-01
"Core Dumped" just means that your program crashed, and it created a debug file (called a core). you can usually just delete these files unless you want to submit to the pidgin devlopement team.

if you get a seg fault now, i recommend uninstalling/reinstalling

---

### Post by infernus_crusher on 2007-09-01
I tried updating Ubuntu, Pidgin still doesn't work.

How do you uninstall pidgin? It's not in the Add/Remove Apps.

---

### Post by infernus_crusher on 2007-09-01
hmm i removed /usr/local/lib/pidgin and reinstalled but it still didnt work.

---

### Post by Adramelech on 2007-09-01
how did you install it again?

---

### Post by infernus_crusher on 2007-09-01
by ./configure, make, and make install from root. the usual way.

---

### Post by Adramelech on 2007-09-01
then try:
sudo make uninstall

If pidgin have the target it will uninstall correctly.

---

### Post by infernus_crusher on 2007-09-01
nope tried dat, installed again the normal way, doesnt work... sigh.

---

### Post by Adramelech on 2007-09-01
hummm if you didnt update libraries then it must be on your configuration, delete your .purple folder on home

---

### Post by infernus_crusher on 2007-09-02
yes dats right. it works now. thx!

but how does .purple make Pidgin not work?

---

### Post by finer recliner on 2007-09-02
something happened that corrupted your .purple file (personal configuration settings for pidgin)

most apps have a .nameOfApp in your home folder. if it becomes corrupt (example: syntax is wrong) the application will not run correctly.

in the future you can try this if you suspect its the .nameOfApp file:
```

$mv .purple .purple.bck

```

this command just renames your .purple to .purple.bck. when you run pidgin again, it wont find a file name .purple, so it will generate a fresh new one automatically. if it sovles your problem, then you know the backuped file was the problem. this method can be used for most applications.

---

