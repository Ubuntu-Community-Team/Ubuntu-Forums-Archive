---
title: "Tearing when playing videos"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by steelmole on 2007-12-15
I'm trying to watch some videos but I get tearing.  I also get loads of smearing when moving windows around quickly.  All this seems to be rather graphics related.  Do I need to install graphics drivers?  I've got an intel gma3100.

---

### Post by DrMega on 2007-12-15
I get the same problem on my ATI Radeon 9550. Hopefully someone will be able to point us in the right direction.

---

### Post by gn2 on 2007-12-15
Are you using 3D desktop effects?

Try disabling them if you are.

---

### Post by steelmole on 2007-12-15
Nope, tried enabling them but they wouldn't work.

---

### Post by TheLions on 2007-12-15
try this:

[http://forum.compiz-fusion.org/showthread.php?t=6005](http://forum.compiz-fusion.org/showthread.php?t=6005)

---

### Post by steelmole on 2007-12-15
Isn't that just for if you use compiz though?  I've only tried changing the settings in ubunutu.

---

### Post by TheLions on 2007-12-15
which video player are you using?

try xine and change video rendering options (you must set expert in experience level to change that)

---

### Post by steelmole on 2007-12-15
I've been using totem.  I tried using mplayer and it won't play anything, I get the error "Error opening/initialising the selected video_out (-vo) device."  If I had to say anything, totem looks like its rendering in software, rather than using some sort of overlay like when you use a graphics accelerator.

---

### Post by DrMega on 2007-12-16
> **steelmole said:**
> I've been using totem.  I tried using mplayer and it won't play anything, I get the error "Error opening/initialising the selected video_out (-vo) device."  If I had to say anything, totem looks like its rendering in software, rather than using some sort of overlay like when you use a graphics accelerator.

The default Ubuntu setup uses the GStreamer version of Totem, which (in my opinion) is not great. It does render very slowly as though its using software rendering.

If you go into good old Synaptic, search for Totem, and choose Totem-Xine, it will replace Totem-Gstreamer with Totem-Xine, which works much better. It doesn't solve the tearing though (unless there is some setting in there that helps).

---

### Post by steelmole on 2007-12-17
Now I have to do something to get xvid to play again.  *scratches head*  I wonder what I did last time.

---

### Post by DrMega on 2007-12-17
> **steelmole said:**
> Now I have to do something to get xvid to play again.  *scratches head*  I wonder what I did last time.

You might need to get ffmpeg from Synaptic.

---

### Post by steelmole on 2007-12-17
Synaptic only shows ffmpeg for gstreamer.  Any ideas?

---

