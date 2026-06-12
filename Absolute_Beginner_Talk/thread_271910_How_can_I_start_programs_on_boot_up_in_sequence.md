---
title: "How can I start programs on boot up in sequence?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-10-05
Hi all;

I have 3 programs which I wanted to start during boot-up in sequence: Program 1 start, than prog2 start, then prog3 start, etc..

I’ve added to the Start up program available in gnome.
System > Preferences > Sessions > Startup Programs

But don’t know how to set it so it always boot up in sequence.

Please help.
Thanks,
Kpham.

---

### Post by calvinthomas on 2006-10-05
If you edit the startup file (not exactly sure where it is in gnome) in kde its /home/<username>/.kde/Autostart (have a look in your home folder in Gnome (don't forget to show hidden files/folders)) and then edit the command slightly like this:

Instead of having:

```
#!/bin/bash
/link/to/file
```

Have:

```
#!/bin/bash
sleep t
/link/to/file
```

Where t is replaced by a value i.e. 5 for 5 seconds then you can start them in order i.e. don't set program 1, set program 2 to sleep 5 and program 3 to sleep 10.

There might be a better way but thats the way I do it to stop my dock and conky messing up when I put into XGL & Beryl

HTH

Calv

---

