---
title: "ivtv, cron and gui (mythtv, tvtime)"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-09-06
I’ve managed to setup the ivtv drivers for my Hauppauge 150, and can watch tv on mplayer by using:

```
 mplayer -vo xv /dev/video0
ivtv-tune -c # -d /dev/video0 
```

Installing mythtv using hyame’s guide is unfortunately out of my league -- I’ve also tried TVtime, but it  ‘can’t find /dev/video0’ for some reason. <sigh>

In the end, I don’t mind watching tv by using terminal’s to control it. 

But, I would like to know how I might be able to cron the recording of CSI on Monday’s at 8:00? The commands would be:

```
ivtv-tune -c 25 -d /dev/video0 
cat /dev/video0 > /mnt/hdb1_storage/media/tv/CSI.mpg
```

And if I really wanted to get fancy, how would I automatically add the date into the file name? I’m guessing a ‘string’? something like:

```
cat /dev/video0 > /mnt/hdb1_storage/media/tv/CSI ‘&date’.mpg
```

?

Anyways, if someone could point me in the right direction, that would be much appreciated.

---

### Post by Episteme on 2006-09-08
I've see a few others also looking for something other than mythtv to watch, record and alike using the ivtv drivers.

I found this set of scripts that have done it for me.

[http://tebl.homelinux.com/view_project.php?project_id=69]("http://tebl.homelinux.com/view_project.php?project_id=69")

I'm now editing them to allow me to pause live tv by way of replacing

```
mplayer -vo xv /dev/video0
```

with

```
cat /dev/video0 > /mnt/hdb1_storage/media/tv/temp.mpg
mplayer /mnt/hdb1_storage/media/tv/temp.mpg
```

I'm wondering how to keep the temp.mpg file from getting too big - is there a way to start 'eating' the tale of this file after it reaches a certain size or after a certain time? Not sure if such a command exists.  Right now, I'm working on just rm temp.mpg whenever the channel is changed.

My goal is to 'meld' these scripts, editing them for function (eg. my psudo-pause thing), and using zenity for gui-like interface.  I'm no programmer by any means, and just learning bash now, so any pointers would be appreciated.

Peace,

Sean

---

### Post by dlai on 2006-09-13
The new xawtv supports ivtv... I've made a deb it is right here: [http://ubuntuforums.org/showthread.php?t=170884]("http://ubuntuforums.org/showthread.php?t=170884")

---

