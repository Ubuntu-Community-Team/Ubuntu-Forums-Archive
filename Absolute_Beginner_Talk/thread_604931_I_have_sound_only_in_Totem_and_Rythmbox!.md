---
title: "I have sound only in Totem and Rythmbox!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by TheLions on 2007-11-06
Somebody help!!! ](*,)

Problem is that i have sound only in that two players, nowhere else, not even at startup or other programs(Firefox, Xine, VLC, WINE...).

it's like other outputs are muted, but they ain't!

[[IMG]http://img159.imageshack.us/img159/4299/prikazzaslonawj8.th.png[/IMG]](http://img159.imageshack.us/my.php?image=prikazzaslonawj8.png)

I have second unused sound card(C-media), is it possible that some programs are sending signals to wrong sound card



[ MSI nforce4 ultra based mbo
amd x64 x2 3800
onboard realtek ck804 sound card
C-Media cmi8738 sound card

ubuntu 7.10 x64
]

---

### Post by rudeboyskunk on 2007-11-06
Is wine using OSS or ALSA?  Type "winecfg" into a terminal, and when the window pops up, go to "Audio."  Look and see which is checked off by default.

---

### Post by TheLions on 2007-11-06
Thanks for replay!
ALSA and OSS both are checked!

i get this:

marko@Zvjer:~$ winecfg
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1

---

### Post by TheLions on 2007-11-07
I solved the problem by removing unused(C-media) soundcard from my PC

:):)

---

### Post by mouseboyx on 2007-11-07
Same problem here. Solved same way.

---

### Post by jonju on 2007-11-07
I have a similar problem. But I can't, for some reason, deactivate my on-board sound module. The Bios has the function to disable but it does not seem to work and the BIOS is also the most recent one. Now, Ubuntu seems to be about the only linux distribution which has problems to configure a second soundcard due to the fact that alsaconf has been removed since 6.10. Certain applications such as Totem do send the signal as I selected it, but other such as aplay, system sounds etc go still over the on board sound module.

---

### Post by TheLions on 2007-11-09
which bios?
which mainboard?
which scard?

---

