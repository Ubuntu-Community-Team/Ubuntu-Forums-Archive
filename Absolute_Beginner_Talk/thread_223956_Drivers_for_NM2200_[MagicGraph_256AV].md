---
title: "Drivers for NM2200 [MagicGraph 256AV]"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Seren Lino on 2006-07-27
Any clues on where I might find them?

---

### Post by hw-tph on 2006-07-27
In the main repository you'll find the video driver:

```
hakan@devon:~$ apt-cache policy xserver-xorg-driver-neomagic
xserver-xorg-driver-neomagic:
  Installed: 1:1.0.0.5-0ubuntu1
  Candidate: 1:1.0.0.5-0ubuntu1
  Version table:
 *** 1:1.0.0.5-0ubuntu1 0
        500 http://archive.ubuntu.com dapper/main Packages
        100 /var/lib/dpkg/status
```

The default kernel packages should have the snd-nm256 Alsa (sound) module in it.

Type **modinfo snd-nm256** to see if it's installed. If it's not the output will be blank. More info about the sound module can be found [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256).

Håkan

---

### Post by Seren Lino on 2006-07-27
Thank you! :)

---

