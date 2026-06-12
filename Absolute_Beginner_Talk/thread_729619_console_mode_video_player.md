---
title: "console mode video player"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by robfindlay on 2008-03-20
Is there a console mode video player for Ubuntu that will actually play a video on the console screen?

-R

---

### Post by p_quarles on 2008-03-20
MPlayer can run without X. Is that what you mean? (people use the word "console" to mean different things, hence my uncertainty about what you are asking).

---

### Post by robfindlay on 2008-03-20
Must read the man file then!  When I run it all I get is audio and no video output.


-R

---

### Post by mcduck on 2008-03-20
You need to also either enable framebuffer, or use some text-mode output for mplayer.

By default the console is text-only environment.

```

mplayer /path/to/file.avi -vo aa
```

---

### Post by robfindlay on 2008-03-20
> **robfindlay said:**
> Must read the man file then!  When I run it all I get is audio and no video output.


-R

I hit cntrl-alt-f1 and then try mplayer and ever codec argument I try I get this: 

Playing BABYLON_5_LOST_TALES.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  480x270  12bpp  29.970 fps  381.6 kbps (46.6 kbyte/s)
Clip info:
 Software: MEncoder 2:1.0~rc2-0ubuntu1~gutsy1
 Source Form: DVD ripped by acidrip.sf.net
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 32.0 kbit/2.08% (ratio: 4000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 270 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 480x270 => 480x270 Planar YV12
gnome_screensaver_control()13 ct: -0.659 972/972 12%  0%  4.7% 6 0 
Exiting... (Quit)


No video...do i have to kill GDM all together?  

what am I doing wrong here...

---

### Post by jseiser on 2008-03-20
two things, I *think* you need X running to use mplayer, you just dont need to launch the front end fo rit

look here

[http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer](http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer)

---

### Post by robfindlay on 2008-03-20
> **jseiser said:**
> two things, I *think* you need X running to use mplayer, you just dont need to launch the front end fo rit

look here

[http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer](http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer)


This works in the console: 
" $ mplayer test.avi -vo svga" 


But all  get on the TV is squiggyly lines.


-R

---

### Post by robfindlay on 2008-03-20
Okay what if I just edited grub to give me the option to boot to a straight console without GD M even running?  

Or the command to kill it comeletely once it's up and running? 

Getting GDM out of the way might be the fix. 

Can someone tell me how to that?

---

### Post by p_quarles on 2008-03-20
Sure. Once you're logged in, hit ctrl-alt-F1 to bring up a TTY. Now, kill gdm by running this:
```
sudo /etc/init.d/gdm stop
```
And it's gone.

To set up a GRUB entry for this mode, you would need to configure one of the unused run-levels. The default run-level is 2, and 3, 4 and 5 are available for custom configurations.

---

