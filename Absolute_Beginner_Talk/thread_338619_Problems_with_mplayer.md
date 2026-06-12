---
title: "Problems with mplayer"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-14
Why can't I reproduce video on mplayer?  every time I try (I've tried with different MPEG videos) it appears this message:
[CENTER]Fatal error!
Error opening/initializing the selected video_out (-vo) device.
ok[/CENTER]

---

### Post by taurus on 2007-01-14
What's the first screen of text from this command from a terminal?

Applications -> Accessories -> Terminal
```
more ~/.mplayer/gui.conf
```

---

### Post by Jorge32 on 2007-01-14
```
enable_audio_equ = "yes"
vo_driver = "xmga"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "yes"

```

---

### Post by taurus on 2007-01-14
```
gedit ~/.mplayer/gui.conf
```
And change this line
```
vo_driver = "xmga"
```
to this.
```
vo_driver = "xv"
```
Save it.  Then, run mplayer from the commandline and see what happens.

```
gmplayer
```

---

### Post by Jorge32 on 2007-01-14
```
jorge@ubuntu:~$ gedit ~/.mplayer/gui.conf
bash: gedit: command not found

```? :confused: 
Is this because I am using Xubuntu?

---

### Post by taurus on 2007-01-14
Yip.  Just replace it with nano.  Didn't know you are running Xubuntu.

```
nano ~/.mplayer/gui.conf
```
(Hold down <Ctrl> while pressing x to exit.  Type Y to save it and then Return key.)

---

### Post by Jorge32 on 2007-01-14
yeah that was it! thanks

---

### Post by taurus on 2007-01-14
> **Jorge32 said:**
> yeah that was it! thanks

Good.

---

