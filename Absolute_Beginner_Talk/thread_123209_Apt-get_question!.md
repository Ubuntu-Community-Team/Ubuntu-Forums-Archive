---
title: "Apt-get question!"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by achafe on 2006-01-29
I'm trying to use apt-get to install programs, mainly a windows manager, from a cdrom into Ubuntu 5.10 server.  I've search google and thought that typing 'apt-get cdrom add' would do the trick, but it didn't go!

Any help would be great!!

Thanks!

---

### Post by psomas on 2006-01-29
can you be more specific?
you want to install programs from a cd that you have?
anyway,here are some tips on instaling new software:
with apt-get you can only download and install deb packages from some specific     
'places' caled repositories...
you can open synaptic and search for a program you want...
if you don't find it you can search on the internet and find the deb package you want...then you can install it using the command dpkg...
or if you find only the source you need to compile it...

---

### Post by astoltz on 2006-01-29
[QUOTE=achafe]I've search google and thought that typing 'apt-get cdrom add' would do the trick, but it didn't go![/QUOTE]You had the syntax a little wrong. I think the correct command is:```
sudo apt-cdrom add
```.

Try "man apt-cdrom" for more info.

---

### Post by benplaut on 2006-01-29
keep in mind that the only window manager (i think) included on the disk is Metacity, which isn't the best choice for a plain WM.

do you have internet on the machine?

---

### Post by achafe on 2006-01-29
I have a couple cd's, that I think might have some kind of windows magers, and everything else I need to get a desktop ruinning in Ubuntu server.  One of these cd's is the Ubuntu Lite iso, from [www.ubuntulite.org](www.ubuntulite.org)

thanks for the tip on the snytax, it worked, of course!

Oh, ...no the machine doesn't have an interenet connection that linux will pick up!

---

