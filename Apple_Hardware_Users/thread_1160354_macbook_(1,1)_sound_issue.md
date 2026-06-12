---
title: "macbook (1,1) sound issue"
date: 2009-05-15
forum: Apple Hardware Users
---

### Post by neverok on 2009-05-15
i'm having a problem with my sound on my macbook after i upgraded to 9.04. i was using 8.04 before and the sound  wasn't working either aT first, but i followed the instructions at this link [http://ubuntuforums.org/showpost.php?p=3764871&postcount=9](http://ubuntuforums.org/showpost.php?p=3764871&postcount=9) and it worked fine. but now i cant get the sound to work. can anyone help me

---

### Post by nathanid95 on 2009-12-05
You could try following those instructions again, or in reverse, or boot into OS X and turn your volume all the way up and try again. I'm not as familiar with the older macbook, if thats what you have.

---

### Post by linuxopjemac on 2009-12-06
did you try to unmute channels in alsamixer pressing "m"?

```
alsamixer
```

---

### Post by Jdutch101 on 2009-12-06
I had a similar issue, where my 1,1 macbook refused to play audio through the headphone jack. I am running Karmic, but you could try downloading and installing ALSA Mixer, from either synaptic or which ever program you use. You should be able to change the volume of the system as well as several other options, including unmuting the headphone jack, if you run into that problem as well...

if you are familiar with terminal there is also a command that will bring up a mixer to control the ALSA driver. I forget what it is, but I'm sure someone else would know, or you could google it.


good luck

---

