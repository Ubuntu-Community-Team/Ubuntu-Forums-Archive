---
title: "Mencoder - change aspect ratio"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-06-14
Hi all....I converted an mpg file to avi using mencoder....

mencoder -oac copy -ovc lavc -o ~/destination.avi ~/source.mpg

The source mpg was 16:9 widescreen. But when using VLC the resulting avi was tall and skinny (0.83:1 as opposed to 1.78:1 if that means anything). 

The picture and audio quality is fine. It's just everything looks tall and skinny.

I fired up gspot on an old Win98 machine and it said the source.mpg is 480x576 which equates with the output avi's appearance.

When I play the source mpg in mplayer it says:

VDec: vo config request - 480 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 480x576 => 1024x576 Planar YV12 

....and then plays the source.mpg fine.

Anyone offer any advice as to how to get the destination.avi to look right.

Many thanks
Miguel

---

### Post by tito13kfm on 2007-06-15
The problem results from encoding your anamorphic MPG file to an AVI and it not saving the setting to be displayed back properly in your video player.  A quick fix to this in VLC is to right click the playing video, select aspect ratio, and change it from default to 16:9.

For playback in mplayer do this
mplayer -aspect 16:9 movie.avi

---

### Post by Miguellint on 2007-06-15
> **tito13kfm said:**
> A quick fix to this in VLC is to right click the playing video, select aspect ratio, and change it from default to 16:9

Thanks for the quick fix, tito13kfm. 

After a bit of googling I finally found an explanation and solution in (surprise, surpise) the MPlayer documentation. 

The MPlayer manual isn't installed by default. I needed to install (via synaptic) the package mplayer-doc. Then look in the usr/share/doc/mplayer-doc/HTML/en/index.html file

For future reference here's the relevant part:

<snip>

13.10. Preserving aspect ratio

DVDs and SVCDs (i.e. MPEG-1/2) files contain an aspect ratio value, which describes how the player should scale the video stream, so humans will not have egg heads (ex.: 480x480 + 4:3 = 640x480). 

However when encoding to AVI (DivX) files, you have to be aware that AVI headers do not store this value. Rescaling the movie is disgusting and time consuming, there has to be a better way!

There is

MPEG-4 has a unique feature: the video stream can contain its needed aspect ratio. Yes, just like MPEG-1/2 (DVD, SVCD) and H.263 files. Regretfully, there are few video players apart from MPlayer that support this MPEG-4 attribute. 

This feature can be used only with libavcodec's mpeg4 codec. Keep in mind: although MPlayer will correctly play the created file, other players may use the wrong aspect ratio.

</snip>

Usage: (should all be on one line)

mencoder source-svcd.mpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:autoaspect -vf crop=714:548:0:14 -oac copy -o output.avi


The resulting avi looks fine in VLC 0.8.6 


Dare I say it..... the RTFM curse of the newbie strikes again :-)

Regards
Miguel

---

### Post by Miguellint on 2007-06-15
> **Miguellint said:**
> 

I fired up gspot on an old Win98 machine... 

And there's no need to do that anymore as Linux finally has an app as good as gspot. 

MediaInfo 

[http://ubuntuforums.org/showthread.php?t=453125](http://ubuntuforums.org/showthread.php?t=453125)

Regards
Miguel

---

