---
title: "Volume is very low on iMac"
date: 2010-03-19
forum: Apple Hardware Users
---

### Post by tyre_ on 2010-03-19
I have an iMac running OSX and my sound is working in Ubuntu 9.1 but the volume is just really low so that's pretty annoying.  I have built in Intel High Def Audio.  Can anyone help me out with this one, I'm REALLY new to linux so can you give me barney style instructions please :)

---

### Post by linuxopjemac on 2010-03-19
you could have a look if with alsamixer you could make the output higher:
```

alsamixer
```

---

### Post by tyre_ on 2010-03-19
> **linuxopjemac said:**
> you could have a look if with alsamixer you could make the output higher:
```

alsamixer
```
I turned everything up to max with alsa mixer but it's still very quiet.

---

### Post by linuxopjemac on 2010-03-19
what kind of iMac do you have ?

---

### Post by tyre_ on 2010-03-19
I have iMac 8,1 with Intel, running OS X 10.5.4

---

### Post by linuxopjemac on 2010-03-20
can you give me the output of:

```
uname -r
```

---

### Post by tyre_ on 2010-03-20
```

2.6.31-20-generic

```

---

### Post by linuxopjemac on 2010-03-20
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

then reboot, check alsamixer if your channels are not muted and try again if you have better sound.

---

### Post by tyre_ on 2010-03-20
Unfortunately the volume still isn't at it's full potential.  I have Bose speakers that hook up through the mic jack and I should be able to blow myself away.  But the computer speakers themselves aren't working at all.  I apologize I just now tried unplugging the Bose and didn't realize that the computer speakers weren't even working.

---

### Post by tyre_ on 2010-03-21
Alright I was finally able to fix this.  I'll tell u what I did maybe u can help someone else out with it.

Logged on as root user I went to /etc/modprobe.d/alsa-base.conf and added
options snd-hda-intel model=mbp3
to the very end of the file.

my soundcard wasn't actually listed so i picked the closest one to it which was ALC888/885 or something like that and the model for it was mbp3 and it worked out.

computer speaker and mic are working great.

---

### Post by tyre_ on 2010-03-21
by the way, thanks for your help!

---

### Post by scotthep on 2010-03-24
Thank you tyre_ that worked perfectly on an iMac 7,1

---

