---
title: "Reinstalling Ubuntu, need help"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Keitarosan on 2007-06-11
I'm going to reinstall Ubuntu because after a month of trying to get my wireless internet to work, I think I've messed it up too much. I tried different guides, and now Wireless doesn't even appear as an option in Network. I am going to reinstall and try again.

I am dual-booting Ubuntu and Windows XP, and I don't want my reinstallation to affect Windows XP, so could someone tell me how to uninstall Ubuntu, do I do it from the CD.

---

### Post by locke.dragon on 2007-06-11
1. back up all your data to cd
2. go here, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and download the gparted live cd
3. burn it to disk like you did with the ubuntu live cd
4. open your cd drive
5. shut off your computer
6. put the newly burned disk in the drive
7. follow the on-screen instructions
8. delete your current ubuntu partitions
9. go into the ubuntu live cd and hit "install in largest contiguous space" 
10. then just stick your data back in the new install
11. follow this tutorial, [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) to make future re-installs easier

hope this helps.  i've re-installed many a time using this exact method.  it is by far the easiest and most effective way to do it.

---

### Post by brim4brim on 2007-06-11
Shoudn't Gparted already be installed on the Live CD so you can delete the partitions before you double click install at all?

If its already installed, it'll save you a CD and time.

---

### Post by locke.dragon on 2007-06-11
yeah.  it's on there, but it won't delete ubuntu partitions.  i've tried many times, but it's always locked.  it's easier to just use the gparted live cd.  it's easier and i find that it's more reliable anyway.  (not to mention faster because there are no other bells or whistles involved)

---

### Post by Keitarosan on 2007-06-11
This is the first time I've tried burning something on Ubuntu, what do I use to burn an ISO?

---

### Post by locke.dragon on 2007-06-11
the best way is to use k3b.  go to Applications>>Add or Remove Programs and search for K3B.  it's a cool app that get the job done in a quick and efficient way.  just make sure you burn it at the lowest possible speed (mine can burn down to 10x, that's still pretty fast, but the cd still works.)  there's an option in the k3b gui (graphical user interface) that will let you burn an iso.  just follow the instructions and you'll be on your way in no time.  by the by, which ubuntu version do you currently have?  feisty's better than edgy just in case you're still with the last version.

---

### Post by Keitarosan on 2007-06-11
I'm using Feisty, and I'm burning it now.

---

### Post by Keitarosan on 2007-06-11
Okay, I've burned the CD, but I can't figure out what to do next. You said to boot in gparted, but I'm not sure how to do that :(

---

### Post by locke.dragon on 2007-06-11
remember how you first booted into the ubuntu live cd?  just do that, only this time, use the gparted cd you just burned.

but, before you do, from withing your current ubuntu install, could you go to System>>Administration>>Gparted (or "gksudo gparted") and post a screenshot?  that way i can tell you EXACTLY what to do.

---

### Post by Keitarosan on 2007-06-11
Gparted isn't in my Administration, and when I put "gksudo gparted" (without the " ") it asks me for my password, but nothing happens.

---

### Post by locke.dragon on 2007-06-11
have you tried typing

```

gksudo gparted

```

hit Alt>>F2 and type the above into the run diologue that just opened

if that doesn't work, open a terminal and type the above code into a terminal

---

### Post by Keitarosan on 2007-06-11
Yeah I've tried that, should I try "sudo apt-get install gparted"

---

### Post by locke.dragon on 2007-06-11
yeah.  try that and then re-try the code i gave you in my last post.

---

### Post by Keitarosan on 2007-06-11
[[IMG]http://img528.imageshack.us/img528/923/screenshot3gq0.png[/IMG]](http://imageshack.us)

---

### Post by locke.dragon on 2007-06-11
ok.  now go into the gparted live cd and delete the two partitions on the right.  NOT the ntfs one.  you won't be able to access the internet from gparted, so it'd be a good idea to print out some of our posts so you can make sure you do the right stuff.

---

### Post by Keitarosan on 2007-06-11
What do you mean the two on the right? /dev/hda2 and /dev/hda5?

---

### Post by locke.dragon on 2007-06-11
yeah.  actually delete hda2, hda3, and hda5.  i didn't see the extended partition at first.

---

### Post by Keitarosan on 2007-06-11
Everything worked, thank you

---

### Post by locke.dragon on 2007-06-11
you're very welcome!  :)  glad i could help.  ;)

---

