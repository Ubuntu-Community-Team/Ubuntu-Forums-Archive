---
title: "Zbrush 3 on WINE?"
date: 2007-05-27
forum: Art &amp; Design
---

### Post by mech7 on 2007-05-27
Has anybody been able to run zbrush 3 on WINE? With me it complains about vcomp.dll even when i copy it over from windows :(

---

### Post by slegrand on 2007-11-07
copy vcomp.dll from a windows install to your zbrush install directory. Zbrush.exe will find it there, however, it still has issues with the actual dll once it finds it...

---

### Post by smartalecks on 2007-11-07
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8023&iTestingId=12117](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8023&iTestingId=12117)
doesn't look too promising :C

---

### Post by slegrand on 2007-12-12
I have Zbrush running under wine 0.9.50 on ubuntu 7.10 x86.

Quick highlight of how it was done there:

[http://slegrand.blogspot.com/2007/12...ntu-linux.html](http://slegrand.blogspot.com/2007/12...ntu-linux.html)

---

### Post by [Po]lentino on 2008-02-26
> **slegrand said:**
> I have Zbrush running under wine 0.9.50 on ubuntu 7.10 x86.

Quick highlight of how it was done there:

[http://slegrand.blogspot.com/2007/12...ntu-linux.html](http://slegrand.blogspot.com/2007/12...ntu-linux.html)
The link you've posted isn't complete :P:P
This is correct:

[http://slegrand.blogspot.com/2007/12/zbrush-3-working-under-ubuntu-linux.html](http://slegrand.blogspot.com/2007/12/zbrush-3-working-under-ubuntu-linux.html)
Or better, cut and paste:

[http://slegrand.blogspot.com/2007/12/zbrush-3-working-under-ubuntu-linux.html](http://slegrand.blogspot.com/2007/12/zbrush-3-working-under-ubuntu-linux.html)

---

### Post by MajinKa on 2010-01-06
Hey!

Yeah! I can safely say that ZBrush 3 runs as smooth as candy on Wine. I'm using Wine 1.2 (which is not even stable yet) on Ubuntu Karmic.

Here are the specs as to my machine: 4 GB w/ 12Mb Cache, Intel Extreme Quad 2.06, nVidia 260M SLI Enabled (1GB Dedicated)

And here's the best bit of it all, I actually shook... I was able to run not only ZBrush, but THREE instances of ZBrush, two of them with the mesh pushing 3.5 million points... PLUS... Two Maya 2010 loaded with animation, shadows, reflections and one batch Rendering 1K Targas. And yeah, SongBird, GIMP and ofcourse... FireFox (this is happening NOW) 

This ain't me trying to tops the system or burn my GPU, this is just me working and being curious about instancing such loaded apps ;)

Believe!!!

-Kudos

.:MajinKa:.

---

### Post by slegrand on 2012-01-18
Zbrush 4 is as easy as installing on windows and seems to work flawlessly too.
Sorry if my old post about installing it got taken down it was really outdated and I was telling people to do things to their wine installation which technically violate M$ licenses. But these days, none of that is needed anymore, just install and run.
You may need winetricks to install some basic stuff like the VC redistributable, but that's about it. I promise to update the post asap.

EDIT: That counts for ZB 4.0, 4R2 but I haven't tested the latest version with fur.

---

### Post by overdrank on 2012-01-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

