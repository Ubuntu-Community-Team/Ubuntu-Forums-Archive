---
title: "Amarok"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by nelson2006 on 2006-04-29
[SIZE="3"]Hello everyone, I know that kubuntu (KDE) has amarok as their best player, but my question is does amarok work ok on ubuntu (GNOME)? Thank you.[/SIZE]

---

### Post by aysiu on 2006-04-29
Yes, AmaroK works on Gnome.

A few *caveats*, though:

1. It will take longer to load up in Gnome than in KDE. Once loaded up, it should play just fine, though.

2. I haven't tested this yet in Breezy, but in Dapper, if you dragged a song from AmaroK to the Gnome desktop, it would *move* the song file there instead of *copying* it there. In KDE, of course, the song gets *copied*.

3. It may look ugly and not integrate well with the look and feel of the rest of your desktop experience in Gnome.

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]Ok, but if I need to uninstall it in a future, will I confront any problems? Thank you.[/SIZE]

---

### Post by aysiu on 2006-04-29
If you are ever thinking you might want to uninstall AmaroK in the future, make sure you use *aptitude* and **not** *apt-get* or Synaptic to install it. That way, when you uninstall it, you'll also uninstall all the other dependencies that came with it:

Applications > Accessories > Terminal ```
sudo aptitude update
sudo aptitude install amarok
``` Later, if you want to remove it ```
sudo aptitude remove amarok
```

Once again, I repeat, do **not** do ```
sudo apt-get update
sudo apt-get install amarok
``` as this following command will remove only AmaroK and not its accompanying packages: ```
sudo apt-get remove amarok
```

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]Thank you very much, aysiu!!! I like xmms a lot but plenty of peolple like to use amarok. That is why my curiousity :mrgreen: .[/SIZE]

---

### Post by stoeptegel on 2006-04-29
What's with this aptitude aysiu? I know the program, but i didn't knew it did dependencies in a better way.

---

### Post by aysiu on 2006-04-29
[QUOTE=stoeptegel]What's with this aptitude aysiu? I know the program, but i didn't knew it did dependencies in a better way.[/QUOTE] It does. Read more [here](http://www.ubuntuforums.org/showthread.php?t=164082).

---

### Post by stoeptegel on 2006-04-29
Interesting... :)
If i get it right, leftover packages that aren't linked to another get also removed with aptitude, while apt-get remove does just remove the package. 

Looks like i am gona play with aptitude for a while and see how i like it.

---

### Post by RCKola on 2006-04-30
I am trying to run Amarok on 5.10 breezy on an iBook g4, here are the problems:
-Amarok will not start when i have my iPod mounted
-when i try to use Amarok to connect to my iPod, it closes.](*,)

---

