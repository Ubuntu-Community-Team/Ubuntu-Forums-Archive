---
title: "Totem could not play 'vcd://'"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-09-29
I am trying to play a vcd in my linux system. When I am inserting the vcd, it automatically launching the associated program but I am getting an error message, 

-- Totem could not play 'vcd://'. No URI handler implemented for "vcd"

what is the problem?

regards

---

### Post by sbergman27 on 2006-09-29
> **Linux Lover said:**
> I am trying to play a vcd in my linux system. When I am inserting the vcd, it automatically launching the associated program but I am getting an error message, 

-- Totem could not play 'vcd://'. No URI handler implemented for "vcd"

what is the problem?

regards

The problem is that, in my opinion, Totem is next to worthless.

Install vlc, and if you like, mozilla-plugin-vlc.

It will actually do what you want most of the time instead of telling you why it can't.

You may have to enable the Universe or Multiverse repositories in Synaptic to get it.

Settings->repositories

---

### Post by jorn on 2006-09-29
The VLC-media player might do do it.
I installed it plus the codecs via :
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Linux Lover on 2006-09-29
Downloaded and installed. Working too... but not well.

Apparently the video is going smooth but the included audio is not going smooth. Several milli seconds cut is available in the audio portion. I tried to enhance the cache size by 1024. but problem is not solved.

I am using ASUS V3005 AGP card with independent 32MB VRAM and 256MB RAM in my machine.

Also to be mentioned that the same video(I mean the video and the included audio too) is going smooth in WIN.

So far, I also come to know from the documentation that...

-- "VLC does not use the codec packs you might have installed. It comes with its own codecs. If there is no open-source decoder for the format you are trying to read, it won't be supported. (There is an exception, under Windows, for codecs that use the DirectShow framework)."  [Ref : [http://www.videolan.org/doc/play-howto/en/ch03.html#id290893](http://www.videolan.org/doc/play-howto/en/ch03.html#id290893) ]

what to do, please help...

---

### Post by qyot27 on 2006-09-29
> **Linux Lover said:**
> Also to be mentioned that the same video(I mean the video and the included audio too) is going smooth in WIN.
I'm sure much of that speed difference is from the presence of DirectX when using Windows.

Seeing as how you're trying to open a Video-CD - you need support for MPEG-1 video and MP2 (MPEG-1 Layer 2) audio. Totem will support those if you install the right gstreamer plugins, but I don't know which one(s) that would be since I don't use Totem.

I'd try using mplayer.  I've found it to be far less problematic - even on Windows - than VLC is.

---

### Post by Linux Lover on 2006-09-30
mplayer cannot recognize the .dat files even. I am not able to select the files for play.

---

### Post by rykel on 2007-03-06
Hi,

I am also irritated by the inability of Totem to play VCDs... in fact, neither VLC nor MPlayer makes the cut as they are unable to play the audio properly and the user interface is not as easily accessible as Totem respectively.

Is there not a way to enable Totem to play VCDs? Since it CAN play the .dat files that have been copied to the hard disk...

Speaking of which, why is it that until 2007, GNOME is still not able to simply drag and drop the VCD .dat files to the desktop like Windows is able to? Yet another frustration for people in my part of the world, where we have collections upon collections of legacy VCDs.

---

### Post by panch0 on 2007-03-07
"mplayer vcd://" works great for me. Try it out. If that works, there is a nice KDE frontend called KPlayer that adds a nice interface to MPlayer, so check it out too.

---

