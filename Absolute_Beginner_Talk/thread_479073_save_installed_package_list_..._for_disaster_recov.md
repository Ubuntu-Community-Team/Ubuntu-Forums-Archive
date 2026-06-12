---
title: "save installed package list ... for disaster recovery"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2007-06-19
This may be somewhere on the forum, in some slightly different context, so sorry in advance if so.

I just upgraded to Feisty, I had to do a fresh install of everything because I was one release back
(end of the academic year is a busy time).  So I did my usual backup -- all of my personal files, on
DVD -- formatted the partition and did a fresh install.  Then I spent about a day getting back all of
the little bits of software I have downloaded (mostly just by clicking on things in synaptic, but not
entirely), so my new system was usable in the usual way.

So, my question is: can I save off a file which shows all of the packages I have added?  I could put
this on the same DVD as my personal files (or another), then I would use it as follows:
1) In case of hardware disaster, I would fix the hardware problem, do a fresh Feisty install, copy my
/home off the DVD, and then automagically have all of the packages I've chosen as important download
and install.  Note I do fairly frequent personal backups, so this would allow me to recover -- completely
and relatively painlessly -- from problems.
2) Next upgrade, particularly if I miss a step and have to do it by a complete fresh install, I would follow
the same process.

Basically, I am suggesting a fresh install, plus an automagic installation of my personal favorite
packages, would be a great aid to shorter backups.  So -- any way to dump this list of my packages?
In a form from which I can then re-install them, *without simply typing the list*?

Another wrinkle: what about software which you get some other way, not as a .deb?  For example,
I download/install a lot of things from CPAN, how can I list and then automatically recover them?


Thanks in advance!

---

### Post by Cypher on 2007-06-20
Any .DEB packages that are installed can be listed with 'dpkg -l' at the command line. You can use
```

dpkg -l | awk '{print $2}'

```
to get the specific package names on seperate lines. When you wanted to re-install the packages you'd pass these package names back to "apt-get install" and it would bring back the packages. There will be a situation where installing one package will install many of the depedencies and then choosing to install one of those dependency will fail but that'll still be fine in the end.

I don't know of a program that take a list like this and re-installs everything, that'd be an interesting application to write (if I get the spare time)..:)

As far as packages that were installed either as .TAR.GZ, .BIN or something else, then you'd have to save the original archives and re-install them yourself..

---

### Post by shearn89 on 2007-06-20
if you go into synaptice, i think there's an option to either "save current state" (or something similar), or you can click on "installed" and mark all those for reinstall, then file -> save marked changes. I think that works, though not entirely certain...

---

### Post by JonE8 on 2007-06-20
Have a look for aptoncd from the Ubuntu repositories I think that will do what you want for programs installed using add/remove and apt-get.

---

