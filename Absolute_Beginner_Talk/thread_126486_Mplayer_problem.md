---
title: "Mplayer problem"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by mitage on 2006-02-06
my mplayer video playback is jerky and sound skips. I don't have the same problem on XMMS or Rythmbox. Somebody help

---

### Post by macbuff on 2006-02-06
That usually happens when your system isn't up to the task of playing a movie.

John

---

### Post by Jeff250 on 2006-02-06
[http://www.ubuntuforums.org/showpost.php?p=460431&postcount=4](http://www.ubuntuforums.org/showpost.php?p=460431&postcount=4)
That worked for me.

Essentially, at console:
```
sudo gedit /etc/mplayer/mplayer.conf
```
Then try adding the line:
```
srate=48000
```

If I had to throw out a guess, I'd say that this might be necessary because our sound cards handle things natively at 48000khz, so if mplayer outputs at a different rate by default, it has to be converted, hence the jerkiness?  Who knows, but it works for me, so give it a shot.

---

### Post by mitage on 2006-02-06
don't get cute macbuff. my system's a pentium IV cpu with 1 gig of ram

[QUOTE=macbuff]That usually happens when your system isn't up to the task of playing a movie.

John[/QUOTE]

---

### Post by mitage on 2006-02-06
Thanks Jeff. It solved my problem...

---

### Post by Dr. Feelgood on 2006-04-11
Yeah, thanks a ton......I just spent 5 hours trying to fix this frustrating problem.  I should have checked here first!!

---

### Post by Smerity on 2006-04-11
jeff250 - Thanks, fixed up my Mplayer too. The sound was jittery and seemed to cause the video to become jittery too.

Also to note, the fix also fixes Mozilla-Mplayer plugin too.

---

