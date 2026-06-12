---
title: "Sound problems with wmv player"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2006-05-20
-- This is a cross post. Doing it delaberately, just to expand the reach of the question. Apologies if it causes inconvenience. --

Hi there, 

I have downloaded w32 codecs, and seems like configured fine. 

Actually, I am using Ubuntu Dapper drake on an IBM laptop. Actually, when I try playing a file with mplayer (intalled that as well out of desparation), it mentions some kind of Error. I'll try to reproduce the message here...

--- quote ---
It seems there is no Xvideo supprot for your video card available. Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv
See 'mplayer -vo help' for other (non-xv) video out drivers. Try vo x11
-- end quote --
While this message appears, the video is playing find. (though not as good as windows plays the same file), but without any sound...

Does it say something about the problem ?

kindly help.

regards
raghav..

---

### Post by Sef on 2006-05-20
> -- This is a cross post. Doing it delaberately, just to expand the reach of the question. Apologies if it causes inconvenience. --

The defence of "Sorry Officer, I only stole the apple because I was hungry" does not make it right.

Now on to your question:


This may be of interest to you

> XVideo Extension
If your configuration supports XVideo and you do not opt to use GL, then Xtheater will automatically use XVideo for all playback. This provides nice fast, nicely interpolated scaling, allowing one to avoid the unpleasantness of a VidMode switch without horrible frame loss, redraw problems.

What's needed:

    * XFree86 4.0.x, 4.0.3 recommended, included with RedHat 7.1, for one example.
    * Supported Video Card:
          o Intel i810 and i815 - These Supposedly support XVideo out of the box with XFree 4.0.x.
          o Matrox Gx00 chipsets - From what I hear, generally support XVideo with XFree86 4.0.x out of the box, but I have no way to verify this.
          o nVidia chipsets - Supposed to support XVideo with their provided binary drivers, but this also I have no way of verifying myself.
          o ATI Radeon, Rage128 and Mach64 - I have heard people to say have some XVideo support, but again I cannot verify this. You may need to get drivers from the GATOS project. Also, the DRI project may have useful files for some ATI chipsets, but I have no personal experience with this.
          o 3Dfx Voodoo Banshee/3/4/5 - I have heard work with 4.0.3 and above, but I know for a fact that 4.0.3 does *not* work out of the box. A newer version of the DRI is needed from the DRI project homepage. I use 0.7 myself. The Extras and tdfx downloads are of interest here.
          o Savage Chipsets - See [http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html) for more information.
          o Other Chipsets - I have no information on other chipsets, but if they are supported and you know it, let me know. 

If you can not get the XVideo extension to work with your card, but can have support for hardware OpenGL or Mesa 3D support (i.e. Sun 3D chipsets under Solaris 8), then the GL support for MPEG playback may be of interest.


[http://xtheater.sourceforge.net/user-guide/xvideo.html]("http://xtheater.sourceforge.net/user-guide/xvideo.html")

So what chipset do you have?

---

