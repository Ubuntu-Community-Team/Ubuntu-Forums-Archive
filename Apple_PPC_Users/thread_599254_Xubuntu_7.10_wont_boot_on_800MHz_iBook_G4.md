---
title: "Xubuntu 7.10 wont boot on 800MHz iBook G4"
date: 2007-11-01
forum: Apple PPC Users
---

### Post by zadatak on 2007-11-01
The live CD would just go to a black screen and do nothing. I used the "live-nosplash-powerpc" option and got it to boot. Now after i installed it, it does the same thig, just goes to a black screen, but there doesn' seem to be any way to enter any custom boot option or anything. Any way i can get it working?

---

### Post by zadatak on 2007-11-01
Got it working. For anyone who wants to know, i booted up the livecd and changed "splash" to "nosplash" in yaboot.conf and then ran 

```
sudo ybin --config /media/disk/etc/yaboot.conf -v
```

and now it boots!

---

### Post by gl0wst1ckn1nja on 2007-12-17
> **zadatak said:**
> Got it working. For anyone who wants to know, i booted up the livecd and changed "splash" to "nosplash" in yaboot.conf and then ran 

```
sudo ybin --config /media/disk/etc/yaboot.conf -v
```

and now it boots!

hahahahahhahahahahahahaha

i ran this on my mac to get a nosplash boot

this was one of the commands returns

```
ybin: Blessing /dev/hda2 with Holy Penguin Pee...
```

my god this made me laugh

:lolflag:

---

