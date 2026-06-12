---
title: "Quick dosbox question!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-15
WTF!
I've installed the dos game I wanted (Master of Magic) and I've installed dosbox.
My Question is, from the HowTo's I've been on, it instructs me to mount stuff, WHAT?!?!

Someone please clarify this for me, all this mounting!

---

### Post by Parasitesss on 2007-04-15
It says to mount stuff on my D drive, I DIDNT KNOW UBUNTU HAD D DRIVES!!!

---

### Post by david_kt on 2007-04-15
First of all, please put you dos games in one folder in you home folder, lets say the name of your folder is dosgames. Open a terminal, and type:
```

 dosbox <enter>
```

That will open another terminal. On the new terminal type:

```
mount c dosgames
```

That will mount your dosgames folder to dosbox as drive c. After that, go to drive c:

```
C: <enter>
```

And the rest is the same as what you did in DOS.

DK

---

### Post by Parasitesss on 2007-04-15
I really don't understand :'[
What other drives does ubuntu have?

---

### Post by Parasitesss on 2007-04-15
[IMG]http://i11.tinypic.com/2dv92mv.png[/IMG]

---

### Post by Perfect Storm on 2007-04-15
Try this guide: [http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)
It contains a nice gui with good options.

Picture of it:
[[img]http://www.imageviper.com/displayimage/78381/0/DosboxGameLauncherPre.png[/img]](http://www.imageviper.com/displayimage/78380/0/DosBoxGameLauncher.png)

normally you can also do;

write **dosbox** in the terminal and then drag MoM's .exe file into the terminal and then hit enter.

---

### Post by Parasitesss on 2007-04-15
referring to david_KT I don't have a straight forward MasterofMagic.exe file in the /home/john/dosgames!
Which means I **cant** simply do

> C: cd MasterofMagic.exe

---

### Post by david_kt on 2007-04-15
> **Parasitesss said:**
> referring to david_KT I don't have a straight forward MasterofMagic.exe file in the /home/john/dosgames!
Which means I **cant** simply do

Ok, may be I should do it from the start.
First question is where do you keep your "MasterofMacic.exe" file?

I will continue after I know where your file is.

DK

---

### Post by the.unclean.cpp on 2007-04-15
Try this tutorial: [http://hack4more.blogspot.com/2007/03/first-of-all.html](http://hack4more.blogspot.com/2007/03/first-of-all.html)

---

### Post by Parasitesss on 2007-04-16
Thanks to all who helped me out, but I got this resolved, thankyou once again.

---

