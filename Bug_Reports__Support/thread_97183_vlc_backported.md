---
title: "vlc backported?"
date: 2005-11-30
forum: Bug Reports / Support
---

### Post by quinnman on 2005-11-30
Hallo. I have browsed through backports and vlc is listened there, but it is not available through synaptic. This might be a "bug".

---

### Post by Bachstelze on 2005-11-30
Is your sources.list up-to-date ?

---

### Post by quinnman on 2005-12-01
[QUOTE=HymnToLife]Is your sources.list up-to-date ?[/QUOTE]
I think so, but anyway, how can I find out?

---

### Post by InsanePenguin08 on 2005-12-01
I've had a problem trying to apt-get vlc as well, it says that it cannot find the package:
```
eric@linux-box:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc

```

---

### Post by InsanePenguin08 on 2005-12-01
Well, I searched the forums again. 

Try [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

It worked for me, at least to get VLC.

---

### Post by jdong on 2005-12-01
hmm, doesn't look like i386 package went through... allow me to investigate that tomorrow... most like just have to send it through a rebuild.

---

### Post by quinnman on 2005-12-07
[QUOTE=InsanePenguin08]Well, I searched the forums again. 

Try [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

It worked for me, at least to get VLC.[/QUOTE]
I have checked my source.list and it is up-to-date. I also looked at the backports server and I am able to see there several versions of vlc:
vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (I have currently installed)
vlc_0.8.4-svn20051025-0ubuntu1~breezy1_amd64.deb (no i386 version)
vlc_0.8.4.debian-1ubuntu1_i386.deb (this lookes like the version I want, probably it is the final version 0.8.4)
Any idea?

---

### Post by jdong on 2005-12-07
This is a known issue. I e-mailed the build administrator upstream around the 29th of November, and have not got a reply yet. I followed up in IRC about the 8 backports still not done (ranging from 5 to 10 days old) and he has acknowledged the situation and asked for us to be patient.

So, we shall wait :)

---

### Post by quinnman on 2005-12-07
Thank you jdong for reply. I'll try to be patient :-)

---

