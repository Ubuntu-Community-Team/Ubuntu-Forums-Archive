---
title: "[SOLVED] Can't boot or mount Ubuntu 8.04 CD on G5"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by fizikz on 2008-08-11
I've burned a copy of the Ubuntu 8.04.01 CD in linux and both my G5 (PPC) and a MacBook Pro (Intel) won't mount it when the CD is inserted. I'm not sure how to mount it manually. When I try to boot from it on the G5, I hear the CD spin up, but after some delay the computer just boots into OS X normally. Any help?

---

### Post by stream303 on 2008-08-11
Just in case there's something missed:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Both Windows and OSX details are included.  Be sure to burn at a low enough speed for your G5 to read.  Use CDR-R and not CD-RW media etc...

I'm assuming you are trying to boot from the internal drive and not from an external firewire....

---

### Post by fizikz on 2008-08-11
I believe I followed the procedure outlined there, except that the speed may have been at maximum... Could that really cause the disc not to be readable by Mac drives? It mounted just fine on a Windows machine and in linux.

---

### Post by cyberdork33 on 2008-08-11
> **fizikz said:**
> I believe I followed the procedure outlined there, except that the speed may have been at maximum... Could that really cause the disc not to be readable by Mac drives? It mounted just fine on a Windows machine and in linux.definitely. I have found Mac CD ROMs to be most picky about such things.

---

### Post by stream303 on 2008-08-12
When those cd's mount on your other boxes, are you seeing them as just one big *.iso file, or do you see a whole hierarchical filesystem on them?

If it is just one big iso file, you aren't burning the images as an iso, but merely copying the file...just checking...

And be sure that for your G5, you are actually burning the PPC version, and not the Intel version.  Might be easy to get them mixed up in your multi-arch environment..

---

### Post by fizikz on 2008-08-12
Thanks! I burned another copy at the lowest speed and it worked. Just as a note, I had to use "live-powerpc64 video=ofonly" for it to boot, otherwise it would just hang at a blank screen.

---

### Post by stream303 on 2008-08-13
Great!  Glad to hear it is up and running.  My G5 iMac would do the same thing with the black screen, but would eventually bring up the gui if I waited long enough.

If you don't want to enter those parameters at boot all the time, try changing the parameters in the "append=" line in your /etc/yaboot.conf file.

```
gksudo gedit /etc/yaboot.conf
```

Then, make the system aware of your change to yaboot.conf with:

```
sudo ybin -v -C /etc/yaboot.conf
```

I've got a strange feeling that just the addition of nosplash will be all that is necessary, but you could also try video=ofonly like you did at first (or use both).

That slow-speed burn has bitten many new users, myself included when I first started...

---

