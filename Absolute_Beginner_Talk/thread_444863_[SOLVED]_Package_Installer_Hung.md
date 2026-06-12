---
title: "[SOLVED] Package Installer Hung"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-15
I started ti install virtual box and all was proceeding quite nicely - it needed to download a couple of packages which it appeared to do. 

Then i'm not quite sure what happened but it stopped and I can't close it or anything.

How can I stop it and clean up the aborted installation?

I don't want to force a reboot if it's going to cause major problems as I am not sure what it has done before it stopped!!!

---

### Post by forestpixie on 2007-05-15
Bump..

really don't know what to do here

Help please

---

### Post by forestpixie on 2007-05-15
Please help me he squealed 

Ok I rebooted and it's still alive

But can't access synaptic - that told me to

sudo dpkg --configure - a

which appeared to work 

then trying to rerun package failed as well - screenshot


Then synaptic gave me 

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Any ideas how to clean up so's I can at least get into Synaptic

---

### Post by zvacet on 2007-05-15
```
sudo apt-get --purge remove file_name
```

---

### Post by Happy_Man on 2007-05-15
A lot of people have been complaining with Virtualbox issues lately.... I wonder why?

---

### Post by lebe0024 on 2007-05-15
You're right.  That package manager is hung like a horse!

---

### Post by forestpixie on 2007-05-15
sorry about this but i started another thread - as I was a panicking!!

didn't know how to stop a thread or move it 

wouldn't have left this hanging but i only just noticed it moving 

finally sorting it i think - I'm the circular synaptic error in absolute beginners

? How do you stop a thread in it's tracks?

And I don't think I'll be looking at virtualbox or anything for a while - could of rebooted into win 50 times since i 
 @!*&ed it up

neveer mind only 1 way to learn 

thanks for the help though

---

