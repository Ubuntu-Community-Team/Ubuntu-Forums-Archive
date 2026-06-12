---
title: "Green bar in divx media files"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by bcrom on 2007-04-07
I've installed the w32 codecs as well as the codecs from autmatix, but I still get a huge green bar at the top of all my files encoded with divx 5. Turning on the deinterlacer only makes the line bigger. Also, everything in the video has a blue tint. Does anyone know how to correct this?

---

### Post by xopher on 2007-04-08
What player do you use? Try eg. VLC or mplayer and see if the problem persists.

And I'd install the codecs by hand, not let Automatix bork my system.. check this out:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bcrom on 2007-04-08
This bug happens in every media player: I've tried vlc, Kaboodle, Kaffeine, Ogle, and Mplayer.  I've already installed all the restricted formats as well as every other codec I can find.

EDIT: Oh, and Totem, but no one expects it to work.

---

### Post by r00tintheb0x on 2007-04-08
xopher, you said "not let Automatix bork my system". How do you see/could you see it doing thaT?!

---

### Post by bcrom on 2007-04-08
Okay, I fixed it.  The problem only occurs using beryl/xgl.  When I use gnome, there is no green bar, but the video looks pixelated and awful (I think this is because my xorg.conf is configured for xgl).  

When I use mplayer with xgl it won't work at all and when I use mplayer in gnome, the video won't fullscreen.  I finally got mplayer to play videos correctly and go to fullscreen in xgl by editing ~/.mplayer/gui.conf and settting  

```
vo_driver = "xv"
```

I edited /etc/mplayer/ config files and fixed my aspect ratio in mplayer, so now I use it instead of VLC.

Thanks.

---

### Post by Vajk on 2007-04-21
Thanks for the code, it worked for me.
Can you please tell me how did you fix the aspect ratio ?

---

### Post by nphx on 2007-04-23
Just use Songbird, yes it's a video player too.

---

### Post by db9s on 2007-04-26
is there a easy way to get into the gnome session without logging out?

---

### Post by db9s on 2007-05-01
> **bcrom said:**
> 

I edited /etc/mplayer/ config files and fixed my aspect ratio in mplayer, so now I use it instead of VLC.

Thanks.

What exactly were the changes you made?

---

### Post by basdala on 2007-05-10
Same problem here, only with a DELL Dimension 9200 with ATI x1300 graphics running XGL+Beryl. This worked for me:

- MPlayer: Right click -> preferences -> Video -> Activate OpenGL output
- Totem: View -> Deinterlace (I think I writed it right, in spanish is "Desentrelazar")
- VLC: Options -> Preferences -> Video -> Output -> select OpenGL output
- Xine: No fix yet

Hope works for you!!

PS. MPlayer had problems with the movie aspect ratio.

---

### Post by jd_cincy on 2007-12-07
Basdala - Thank you!!!  I've had this problem for a while and changing the VLC settings worked.

---

