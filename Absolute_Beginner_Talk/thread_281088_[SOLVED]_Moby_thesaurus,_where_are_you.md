---
title: "[SOLVED] Moby thesaurus, where are you?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by BigJules on 2006-10-20
Having downloaded the v impressive Moby thesaurus via Synaptic, it shows as installed together with its dependency, the dictd package. So why cant I see it anywhere? :-k

---

### Post by bonzodog on 2006-10-20
it's probably just not on the menu, is all. Try using alt+F2, the 'run program' dialog. Type in 'moby' and see if it launches. If it does, you will need to edit the menu yourself, and add it. Some packages do this -- they don't have the menu item built in.

---

### Post by BigJules on 2006-10-21
No dice, I'm afraid - learning a lot of Linux however :neutral:

---

### Post by cwaldbieser on 2006-10-21
> **BigJules said:**
> No dice, I'm afraid - learning a lot of Linux however :neutral:

In synaptic, find the package and click on the "Properties" button (or right click for the context menu and choose "Properties").  Choose the "Installed files" tab.  look for files that are installed in "/usr/bin".  One of these is probably the name you have to run-- it is case sensitive!

I have a script that might help:
```

$ dpkg -L "dict-moby-thesaurus" | xargs -n 1 | { while read FNAME; do if [ ! -d "$FNAME" ]; then if [ -x "$FNAME" ]; then echo "$FNAME"; fi; fi; done; }

```
If you open up the terminal and paste in that command, it should search your package database for the files in the "dict-moby-thesaurus" package and print out the names of all the executable files installed by the package.

---

### Post by BigJules on 2006-10-27
Thanx for the script - regret it didn't throw up any executables, and the Properties bit showed no executables at all in /usr/bin  or anywhere else.

It did say that it reqd the /dictd package installed, and it is, but I can't seem to get it launched either. I emailed moby directly but no reply and as a newbie am not sure where to go next...?

---

### Post by xtacocorex on 2006-10-27
Have you tried a:
```
which moby
```
or a ```
locate moby | grep bin
```

---

### Post by BigJules on 2006-10-28
Thanx - but again no dice. Both cmds came back to the $ prompt, and same when repeated with sudo?? Very odd...:confused:

---

### Post by izak on 2007-07-31
for anyone else stumbling upon this thread and wanting to use the moby thesaurus, head over to [http://ubuntuforums.org/showthread.php?p=3109769#post3109769]("http://ubuntuforums.org/showthread.php?p=3109769#post3109769")

---

### Post by BigJules on 2007-09-12
SOLVED !   Thanks for this, Izak

---

