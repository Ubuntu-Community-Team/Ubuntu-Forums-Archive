---
title: "Convert Videos for Ipod Touch"
date: 2011-12-17
forum: Any Other OS
---

### Post by veidar45 on 2011-12-17
Hello,

with which program can I convert videos on Ubuntu 10.04 for my Ipod Touch? :) I'm also interested in adding subtitles to the video...

Please help! 


Cheers! :)

---

### Post by bliffle on 2011-12-31
Sorry to see you're getting such a weak response to this, which seems pretty useful. I just started on the iPod adventure, and posted a similar query myself.

I think the answer is 'ffmpeg', it usually is. So I tried 'WinFF' for ease, but it doesn't seem helpful.

---

### Post by WienerWuerstel on 2011-12-31
You could try [HandBrake]("http://handbrake.fr/downloads.php") and see if that Program suits your needs.

---

### Post by bliffle on 2012-01-01
Handbrake seems to have a lot of enthusiasts, so I'll give it a try soon, but IIRC it's not in Synaptic.

Meanwhile, having faith that good ol' ffmpeg will come through for me, I ran this google query:

```
google: ipod ffmpeg video script
```

After winnowing out the old and the lame:

[http://blog.jharding.org/2008/05/encoding-video-for-iphone-with-mencoder.html](http://blog.jharding.org/2008/05/encoding-video-for-iphone-with-mencoder.html)

[http://www.johngirvin.com/archives/encoding-video-for-iphone-using-windows-ffmpeg.html](http://www.johngirvin.com/archives/encoding-video-for-iphone-using-windows-ffmpeg.html)

[http://atomized.org/2005/11/converting-video-to-play-on-your-ipod-with-ffmpeg/](http://atomized.org/2005/11/converting-video-to-play-on-your-ipod-with-ffmpeg/)

[http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs)

[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

[http://rodrigopolo.com/ffmpeg/cheats.html](http://rodrigopolo.com/ffmpeg/cheats.html)

[http://ubuntuforums.org/showthread.php?t=1414943](http://ubuntuforums.org/showthread.php?t=1414943)

[http://slated.org/howto_transcode_h264_for_ipod_with_ffmpeg](http://slated.org/howto_transcode_h264_for_ipod_with_ffmpeg)

[http://thomer.com/howtos/ipod_video.html](http://thomer.com/howtos/ipod_video.html)

I'll look at those later today (the catswhocode site looks good), but in the meantime they make some interesting reading about iPod boundary conditions, such as widescreen.

The OP asked about subtitles (I assume *.srt files) but I wasn't alert for those the first time around. Seems to me that the last time I did that I used VLC, but that was years ago.

---

### Post by fdrake on 2012-01-01
that looks like a pretty scary code! :) url:[http://www.nin9lives.com/blog/ffmpeg-ipod-touch-encoding/](http://www.nin9lives.com/blog/ffmpeg-ipod-touch-encoding/)
```

ffmpeg -y -i input_file.avi -an -v 1 -threads auto -vcodec h264 -b 500k \ 
-bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 \ 
-partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 \ 
-level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq ‘blurCplx^(1-qComp)’ \
 -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k \ 
-bufsize 2M -cmp 1 -s 320×240 -f mp4 -pass 1 /dev/null;

ffmpeg -y -i input_file.avi -v 1 -threads auto -vcodec h264 \ 
-b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 \ 
-deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full \ 
-subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 \ 
-g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' \ 
-qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k \ 
-bufsize 2M -cmp 1 -s 320x240 -acodec libfaac -ab 96 -ar 48000 \ 
-ac 2 -f mp4 -pass 2 output_file.mp4 

```

---

### Post by bliffle on 2012-01-01
> **fdrake said:**
> that looks like a pretty scary code! :) url:[http://www.nin9lives.com/blog/ffmpeg-ipod-touch-encoding/](http://www.nin9lives.com/blog/ffmpeg-ipod-touch-encoding/)


I wouldn't touch that code with a ten foot pole: it's 4 years old (a lot has happened in 4 years), there is NO explanation of WHY parameters were chosen, and the comments from guys who tried to use it are negative.

---

### Post by sgtGarcia on 2012-01-01
You can use ```
arista
``` It has ( or You can download from their website ) preset for Ipod Touch.

---

### Post by FakeOutdoorsman on 2012-01-01
I don't own an iPod Touch, but this should work. Using current recent compiled FFmpeg:
```
ffmpeg -i input -c:v libx264 -preset medium -vpre ipod640 -crf 24 \
-vf scale="640:trunc(ow/a/2)*2" -c:a libfaac -q:a 100 output.mp4
```
[list]
[*]**input** - the input file
[*]**-c:v libx264** - use the libx264 video encoder for H.264 video
[*]**-preset medium** - a preset is a collection of optimized x264 options to provide a certain encoding speed/compression ratio. Generally, use the slowest you have patience for once you determine your *-crf*. A list of presets is available with *x264 --help*.
[*]**-vpre ipod640** - an additional preset that provides some options for picky Apple devices.
[*]**-crf 24** - controls video quality of output. A lower number is a higher quality. Use the highest number that still provides an acceptable quality. A sane range is 18-28.
[*]**-vf scale="640:trunc(ow/a/2)*2"** - the scale video filter will resize your output to a max width of 640 and will use whatever height that will preserve the aspect ratio. It looks complicated because it will automatically round to an even number which is a requirement for libx264.
[*]**-c:a libfaac** - use the libfaac audio encoder for AAC-LC audio
[*]**-q:a 100** - controls audio quality (VBR) of output. Mapped to the "faac -q" option.
[/list]
FFmpeg (or libav) from the repository will use slightly different options:
```
ffmpeg -i input -vcodec libx264 -vpre medium -vpre ipod640 -crf 24 \
-s 640x480 -acodec libfaac -aq 100 output.mp4
```

If you're using an older FFmpeg from the repo then replace *preset* with *vpre*, and if it's even older replace *medium* with *normal*. The syntax may vary between Ubuntu versions, but this should cover most of it. I haven't been keeping up with recent repository versions.

Note that you may have to enable additional encoders in FFmpeg to use libx264 and libfaac, but that's simple to do. See *Option C* in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by andrew.46 on 2012-01-02
> **FakeOutdoorsman said:**
> 
[list]
[*]**-vf scale="640:trunc(ow/a/2)*2"** - the scale video filter will resize your output to a max width of 640 and will use whatever height that will preserve the aspect ratio. It looks complicated because it will automatically round to an even number which is a requirement for libx264.
[/list]


This little piece of syntax blew me away :). Have you thought of adding it in with the other 'scale' example here:

FFmpeg Filtering Guide
[https://ffmpeg.org/trac/ffmpeg/wiki/FilteringGuide](https://ffmpeg.org/trac/ffmpeg/wiki/FilteringGuide)

with hopefully a detailed explanation, I am struggling a little to understand this one :).

---

### Post by FakeOutdoorsman on 2012-01-02
> **andrew.46 said:**
> This little piece of syntax blew me away :). Have you thought of adding it in with the other 'scale' example
I did, actually, but I never got off of my donkey to do it.
> **andrew.46 said:**
> with hopefully a detailed explanation, I am struggling a little to understand this one :).
I'm not the author. It's from Stefano, the FFmpeg Filter Guru. I saw it in a [bug report](http://ffmpeg.org/trac/ffmpeg/ticket/309#comment:3) and promptly stole it.

I was always a math delinquent, but AFAIK:
[list]
[*]**640** - The desired output width.
[*]**trunc** - I suppose this is ignoring any potential decimals, or maybe rounding?
[*]**ow** - This is the easy one. Output width. Same as using *out_w*.
[*]**a** - Same as iw / ih.
[/list]

So, assuming an input of 1280x720 and a desired output width of 640 I think it can be expanded as:
```
trunc(((640 / (1280 / 720)) / 2) * 2)
```

---

### Post by mips on 2012-01-03
> **bliffle said:**
> Handbrake seems to have a lot of enthusiasts, so I'll give it a try soon, but IIRC it's not in Synaptic.

I think you are going to wait a long time before it appears in Synaptic.

Use this PPA to install it: See post below!

Ubuntu 11.10 users should use this PPA [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by JohnAStebbins on 2012-01-03
> **mips said:**
> I think you are going to wait a long time before it appears in Synaptic.

Use this PPA to install it [https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

This is an old PPA not supported by HandBrake and it only has older versions of HandBrake (though we do appreciate djong's early efforts in creating a HandBrake PPA).

PPA's managed by the HandBrake developers are
Releases: [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
Nightly builds: [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

The last release is over a year old and does not build on 11.10, so as mips noted, Oneiric users must use the nightly builds for now.  A new release is in the works...

---

### Post by mips on 2012-01-03
> **JohnAStebbins said:**
> This is an old PPA not supported by HandBrake and it only has older versions of HandBrake (though we do appreciate djong's early efforts in creating a HandBrake PPA).

PPA's managed by the HandBrake developers are
Releases: [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
Nightly builds: [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

The last release is over a year old and does not build on 11.10, so as mips noted, Oneiric users must use the nightly builds for now.  A new release is in the works...

Thanks for clearing that up. If only you got here sooner :)

---

