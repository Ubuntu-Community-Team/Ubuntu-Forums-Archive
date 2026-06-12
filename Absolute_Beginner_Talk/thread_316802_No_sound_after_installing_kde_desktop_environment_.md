---
title: "No sound after installing kde desktop environment in Dapper"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-11
I installed the KDE desktop environment in Dapper (on an Acer Aspire laptop) and now I have no sound anymore.

```
me@ubuntunbk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**Strange behaviour:** I can play audio cd's but the sound is very very quiet even though I have the volume bar on max.

Also...

```

me@ubuntunbk:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
```

Thanks in advance.

---

### Post by PartisanEntity on 2006-12-11
Sorry correction, I do in fact get sound, but it is very very quiet. (Even though volume is set to max).

---

### Post by PartisanEntity on 2006-12-12
bump...

---

### Post by PartisanEntity on 2006-12-14
I noticed that when Ubuntu is booting up or down, it says "alsactl_store failed ..."

This probably has something to do with the error, can anyone please help me out here? Thanks.

---

### Post by PartisanEntity on 2006-12-15
bump

---

### Post by dbd on 2006-12-15
You could try running alsamixer from the command line and turning the volume up to max with that (you want to turn up both the Master volume and the PCM volume levels).

---

### Post by PartisanEntity on 2006-12-30
I still have this issue, volume is very very very low even though I set it to max.

I tried to launch alsamaxer through terminal by entering 'alsamixer' and got this:

> alsamixer: function snd_mixer_load failed: Invalid argument

---

### Post by dbd on 2007-01-02
Sorry, should have read your first post before posting!

Just had a look around the forums and this thread looks like it could be of use:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
and maybe this will be of use too:
[http://www.ubuntuforums.org/showthread.php?t=324247](http://www.ubuntuforums.org/showthread.php?t=324247)

---

### Post by l4lucas on 2007-01-10
i have the exact same laptop, and the exact same problem. Neither of those posts solved the issue.

---

