---
title: "Airport Extreme problem.. Please help"
date: 2007-07-18
forum: Apple PPC Users
---

### Post by quixotes on 2007-07-18
So I am pretty much totally new to Ubuntu. I installed after a string of problems with OSX. I had been thinking about it for a while now. I no longer have my OSX disk but found the Feisty install smooth. 

Now, as far as I can tell from the multiple guides i've read on using fwcutter i am supposed to have an OSX install handy or the disk available. The problem is that I dont have either. 

I have fwcutter but I'm not sure where to go from there. I can connect wired fine, but that is rarely and option for me. Please point me in the right direction. Thanks in advance.

---

### Post by quixotes on 2007-07-18
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

This is the guide I was using.. seemed to work great until I hit this step:

```
sudo apt-get install bcm43xx-fwcutter 
```

responds with :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

The following command : 

```
sudo modprobe bcm43xx
```

Hangs in the terminal. I let it sit for about 15 with no return. Am I just being impatient or is there something that I'm missing? Thanks.

---

### Post by ajmctaggart on 2007-07-18
The problem lies in the fw-cutter has to "cut" the firmware out of the hardware...simply installing fw-cutter doesn't do that...

Here's the best way to get this done in about 2 minutes:

[HTML]http://ubuntuforums.org/showthread.php?t=185174[/HTML]


Please let us know how it works!
ajm

---

### Post by ajmctaggart on 2007-07-18
Sorry, all these fancy tools confuse me...

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by gtcoffee on 2007-07-19
i just installed ubuntu on my powerbook 2 days ago...
and i followed this simple guide to set up my wireless without problem...
Hope this will help u out...

[https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444]("https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444")

---

