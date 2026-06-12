---
title: "Where's the documentation I downloaded?"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-01-30
Hello everyone,
I used synaptic and downloaded some documentation for Perl and Bash and Gcc.
Can someone tell me where it would have got downloaded to, cause I can't find it.

If I may also ask, is there a link someplace that will take me to the generic layout of the Linux (or Debian-Ubuntu) filesystem? I'd like to know where the files are. There seem to be multiple copies of files of the same name all over the place...(for e.g the bash profile.)

Thanks,
Nuttycat

---

### Post by jasmuz on 2006-01-30
Did you check the manpages?

---

### Post by aysiu on 2006-01-30
I think it's in /usr/lib/docs or something like that. Maybe /usr/share/docs
Basically, the only directories I care about are...

/boot so I can edit the Grub boot menu
/etc, which has random config files
/home... that's where my files live
/usr/bin because it has all my executables

---

### Post by matthew on 2006-01-30
[quote=aysiu]/usr/share/docs[/quote]Close. It's /usr/share/doc and then in the directory related to the program you are wanting to find documentation about. i.e. /usr/share/doc/nethack
Sometimes the documentation is in the form of plain text files, sometimes they are contained in tar.gz archives.

---

### Post by cstudent on 2006-01-30
Here's a helpful tip:

In Synaptic look under Settings>>Preferences and make sure the "show package properties in main window" is checked under Apperance. This will give you tab headings, one of which will give you a listing of where everyfile for the that package is placed on your system.

---

### Post by nuttycat on 2006-02-12
Sorry it took so long to reply,

Mathew and Aysiu, 
Thanks, those paths helped me find the documentation i was looking for.

Cstudent- that tip was also useful.

Thanks to everyone here.
-Nuttycat

---

