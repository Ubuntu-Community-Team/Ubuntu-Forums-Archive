---
title: "Multiple Processing"
date: 2007-07-23
forum: Apple PPC Users
---

### Post by matt_pittsburgh on 2007-07-23
I have a RS/6000 PPC that is equipped with the 604e power pc processor.  I finally got Ubuntu 6.06 to install!

I need some expert help from all of you...  My RS/6000 actually has 4 604e processors (quad processor) and 2 gigs of RAM.

Right now, Ubuntu 6.06 LTS is only seeing the first processor.  How do I enable SMP for PPC?  I've seen on some of the posts about how to do this for Intel chips, but how do I do it for Apple/IBM PPC chips?  I don't want to mess up what I've been able to do thus far.

I know I need to compile a new kernel, I believe?  How is this done for PPC systems in 6.06 LTS?

Thanks very much for your help!

---

### Post by stmiller on 2007-07-23
Try this:

$ sudo apt-get install linux-powerpc-smp

That kernel should be smp aware.

---

### Post by FNM on 2007-07-24
I don't know if this is specifically related to my G4 system, but I could never get Dapper to use both CPUs with the Ubuntu-provided SMP kernel. Whatever the problem was, Feisty fixed it.

---

### Post by matt_pittsburgh on 2007-07-24
Thanks for the help.  I'll apt-get the ppc-smp.  Hopefully, that will do the trick.  

FNM -- I'll eventually move to Feisty and it's good to know it has SMP support.  On this old RS/6000, I had to start with 6.06 and then I'll upgrade along through the versions.  For some reason, the service processor which handles software installs on this system could not see Feisty when I installed the CD.  It could only see 6.06 LTS.

Thanks everyone.  Much appreciated!

---

