---
title: "Compiling from source, can't find a package"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by sciencectn on 2007-12-27
I was compiling a package from source when I got an error. It had no configuration file, so I ran make with no problem. I then ran sudo checkinstall when it failed. The output from checkinstall is here:
```
========================= Installation results ===========================
test -d /opt/mpeg_stat/bin || mkdirhier /opt/mpeg_stat/bin
bsdinst -c  -s mpeg_stat /opt/mpeg_stat/bin
make: bsdinst: Command not found
make: *** [install] Error 127

****  Installation failed. Aborting package creation.

```
I googled bsdinst, and its just an ordinary shell script that ubuntu doesn't seem to have.  Is there any way of getting it?

---

### Post by spiderbatdad on 2007-12-27
build-essential from synaptic?

---

### Post by sciencectn on 2007-12-27
WOW I just found the problem. At the top left of the mpeg_stat page it says HP-UX. That's apparently Hewlett Packard's Unix distro and I don't think that source code will even work with Linux. I'll have to ask the makers of the python script requiring mpeg_stat how they got it to work.

---

### Post by SOULRiDER on 2007-12-27
If its compiled you can probably run it, just not make a nice package.

---

### Post by sciencectn on 2007-12-27
Actually I found an earlier version of the script that doesn't require mpeg_stat. It works fine, so I don't see why they wanted the user to go through all the trouble with mpeg_stat for the recent version.

---

### Post by Nano-rus on 2008-02-19
Can you please tell me where you found this script?

---

### Post by sciencectn on 2008-03-03
I got the script here:

[http://theli.is-a-geek.org/blog/static/dpgconv](http://theli.is-a-geek.org/blog/static/dpgconv)


I still haven't gotten this to work. For now, I just use a converter program on windows.

---

### Post by MickLionheart on 2008-03-08
Brutishniggabeasts

---

### Post by sciencectn on 2008-03-12
I just got it to work.

It's as simple as adding the bsdinst to the bash directory, compiling mpeg_stat, and adding mpeg_stat to the bash directory. It runs with no problem.

Bsdinst is here if a anyone needs to know:

[http://webcvs.freedesktop.org/xorg/xc/config/util/bsdinst.sh?revision=1.2&view=markup](http://webcvs.freedesktop.org/xorg/xc/config/util/bsdinst.sh?revision=1.2&view=markup)

I put bsdinst in the /bin directory, compiled mpeg_stat, and put that in the /bin directory and ran the python script.


And Micklionheart needs to lay off the shrooms...

---

