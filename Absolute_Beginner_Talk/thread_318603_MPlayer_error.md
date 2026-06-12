---
title: "MPlayer error"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by DaDiablo on 2006-12-14
Hi.
When i try to play some .avi on MPlayer there is an error
Error opening/initializing the selected video_out (-vo) device.
What i have to do?

---

### Post by Kobalt on 2006-12-14
Hello, 
Is the video only a .avi or is it a Divx ? 
Have you install the multimedia codecs ? > [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

---

### Post by DaDiablo on 2006-12-14
I have installed thease codecs 
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
But the error is still there.
Not only .avy, all movie files: .avi, .vob, .wmv etc :(

---

### Post by DaDiablo on 2006-12-14
I tried with codec from mplayerhq.hu too, but there is same error again :(

---

### Post by BarfBag on 2006-12-14
> **DaDiablo said:**
> I tried with codec from mplayerhq.hu too, but there is same error again :(

Did you install it correctly?  What was your method?

---

### Post by xabbott on 2006-12-14
This is a very simple problem. 

Open MPlayer, right click the screen/main window, click preferences, click the video tab, and now go down the list until one of those drivers plays for you.

---

### Post by DaDiablo on 2006-12-14
xabbott, the problem isn't such sipmle as you thought.
There is no drivers in Preferences/Video

---

### Post by taurus on 2006-12-14
In the "video_out" section of your ~/.mplayer/gui.conf, what does it say?

```
more ~/.mplayer/gui.conf
```

---

### Post by DaDiablo on 2006-12-14
```
dadiablo@dadiablo-desktop:~/Downloads$ more ~/.mplayer/gui.conf
enable_audio_equ = "no"
vo_driver = "xmga"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
sub_pos = "100"
sub_overlap = "no"
sub_cp = "ISO-8859-1"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "yes"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "711"
gui_main_pos_y = "715"
gui_video_out_pos_x = "256"
gui_video_out_pos_y = "192"
```

---

### Post by xabbott on 2006-12-14
Try changing xmga to x11

edit: also, i got mplayer from [http://ubuntu.systemadministrator.org/](http://ubuntu.systemadministrator.org/) just incase you are using a different repo.

---

### Post by DaDiablo on 2006-12-14
Same error :(

---

### Post by taurus on 2006-12-14
Try xv...

```
vo_driver = "xv"
```

---

### Post by DaDiablo on 2006-12-14
Is there any list of avaliable drivers . :(
```
vo_driver = "xv"
```
```
Error opening/initializing the selected video_out (-vo) device.
```
again ... :( :(

---

### Post by taurus on 2006-12-14
You still haven't asnwered this question!  How did you install mplayer?

---

### Post by DaDiablo on 2006-12-14
I download him form official site, configure .. make .. make install
I download codecs from official site too and put them at /usr/local/codecs/
I download skin from official site too and put him at ~/.mplayer/skins/
And then start
and ... error

---

### Post by DaDiablo on 2006-12-14
Am i installed it wrong?

---

### Post by taurus on 2006-12-14
You need to look at the ./configure file again if you build it from source.  Of course, mplayer is available from repos and from automatix2...

---

### Post by leefw on 2006-12-15
I had the exact same problem. Check out [this]("http://www.ubuntuforums.org/showthread.php?t=20039") thread!

[http://www.ubuntuforums.org/showthread.php?t=20039](http://www.ubuntuforums.org/showthread.php?t=20039)

---

