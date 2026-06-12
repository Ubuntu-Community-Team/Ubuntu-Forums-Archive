---
title: "msttcorefonts and andale32.exe"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by insenlysen on 2008-04-21
hi

I am unable to update several packages that I am using in Ubuntu 7.10 as whenever I am running the software update manager it gets stuck with errors due to mssttcorefonts. I tried reinstalling msttcorefonts. When i typed in sudo apt-get install msttcorefonts I get the following error message:

--12:41:34--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving hproxy.iitm.ac.in... 10.93.0.35, 10.93.0.36
Connecting to hproxy.iitm.ac.in|10.93.0.35|:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
12:41:34 ERROR 407: Proxy Authentication Required.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I do to rectify the problem? I do not have any other problems with proxy authenticiation

---

### Post by BrendanM on 2008-04-21
insenlyn, I am far from an expert, but my understanding is that the msttcorefonts package can be sort of weird sometimes because it is not a native Linux package, but rather a fonts package released by Microsoft that has been adapted to install on Linux.

I don't know why that particular package won't update, but if you want to just make sure that everything else updates ok, you should go into Synaptic (the package manager), click the "check all updates" box, and then, before you hit "apply" search for "msttcorefonts" and UNCHECK that one, so that it won't try to update that package. Then, everything else should update just fine.

I doubt you will run into any problems with this method, since it's just a font package, it's not like other software will depend on it.

Please write back if you run into more problems.

---

### Post by skymera on 2008-04-21
An exe?

Would installing WINE help at all?

---

