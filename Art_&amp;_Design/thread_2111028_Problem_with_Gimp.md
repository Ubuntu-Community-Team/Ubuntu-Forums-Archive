---
title: "Problem with Gimp"
date: 2013-01-31
forum: Art &amp; Design
---

### Post by Brad55 on 2013-01-31
I have a question; I have Gimp installed on my laptop but it will not start the error I'm getting is "gimp error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory".

I have had Gimp running before but for some reason it won't now.

I have re-installed it and it didn't help.
Any please.

---

### Post by SeijiSensei on 2013-01-31
Are you trying to install Gimp 2.8 from a PPA rather than the standard version in the repositories?  If I run "sudo apt-get install gimp" on a newly-installed 12.04 machine, it installs libgegl-0.0-0 as a dependency.

You can try installing it directly with "sudo apt-get libgegl-0.0-0".

---

### Post by Brad55 on 2013-01-31
I'm just trying to get Gimp 2.6 to work.

I have tried just installing libgegl-0.0-0 but it did not work.

I have also tried this [[COLOR="RoyalBlue"]from here[/COLOR]]("http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html") and it didn't help.
sudo apt-get update
sudo apt-get purge gimp libgegl* libbabl*
sudo apt-get install gimp
sudo apt-get clean

---

### Post by SeijiSensei on 2013-02-01
> **Brad55 said:**
> I'm just trying to get Gimp 2.6 to work.

I have tried just installing libgegl-0.0-0 but it did not work.

What didn't work?  The installation of libgegl or gimp itself?  Did you still get the same error about the missing libgegl library when you ran gimp after installing libgegl?  Is there a copy of libgegl-0.0.so.0 in /usr/lib?

When you tried to install gimp in the sequence of commands above did apt-get include list libgegl (and libbabl) in the list of additional packages being installed?

---

