---
title: "OS X Partition NOT BOOTING!"
date: 2007-11-24
forum: Apple PPC Users
---

### Post by travnewmatic on 2007-11-24
OS X and ubuntu have been peacfully coexisting on my PowerBook G4 until one day disaster struck.

I think it was around the time that 10.4.11 came out.  Yaboot throws up the apple screen, but i don't hear any sort of hard disk activity. I let it sit there forever, but nothing happens.

 all of my things are on my other partition, well, school stuff at least, and i really don't want to have to reformat that part of my hard drive.

Is there some configuration file that i need to be checking?

HLP PLS!
Thanks!
-Travis Newman

---

### Post by kelbizzle on 2007-11-24
Do you get the turning wheel or just an apple screen? Try booting to the MAC OS X Installation cd that came with your computer and check the hard disk using the Disk utility.

---

### Post by kelbizzle on 2007-11-24
One more thing check the apple site for any firmware updates. Also if you have any devices connected remove those.

---

### Post by travnewmatic on 2007-11-24
Just the apple screen, no turning wheel.
I haven't tried using the os x cd yet, but will try that later on the evening.
I haven't checked for any firmware updates.  even if there were how would i install it if i Can't run OS X?
No connceted devices other than my apple ac adapter.

---

### Post by travnewmatic on 2007-11-27
i ended up reformatting the whole thing with leopard.  For my note-taking, i'm using google notebook, so this kind of thing might not happen again.

thanks for the help guy!
-Travis

---

### Post by jmelton on 2007-11-28
I had the same thing happen to me a couple of days ago after installing Feisty over the weekend.  I was able to fix things by having  the Disk Utility on the Install Disk run a check, as suggested above.  For some reason, right after that, I stopped getting a boot menu and it would go straight into OS X, so I had to use the Ubuntu Install Disk to fix yaboot!  Fortunately, that was pretty simple (just entering "ybin" on the command line, I think).

---

