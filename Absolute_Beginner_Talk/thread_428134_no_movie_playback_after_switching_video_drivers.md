---
title: "no movie playback after switching video drivers"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Billy McCann on 2007-04-30
Hello. 

I recently switched my video driver from the i810 driver to the intel driver (the one in "universe").  Now when I try to play a DVD I get the following error from VLC.  

```
billy@earth:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: AlBOW
libdvdnav: DVD Serial Number: 2942a4b7
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/billy/.dvdnav/AlBOW.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000655d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000ddc8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c12dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c141d
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000342] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87

```

I'm not able to play other media types such as mpg either.  The problem may extend to other media types, but these two are all that I've tested.  

Should I just switch back to the inferior i810 driver?  Or is there a way to reconfigure my current driver to play media? 

 I've tried telling VLC to use a different output (XVideo Output Module, or something like that) to no effect. 

Any insight would be greatly appreciated.  I like being able to view media on my computer.  :confused:

---

### Post by LuisGMarine on 2007-04-30
Have you installed any of the codecs?

For example, when you installed vlc, you should have used this code:
```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

To get some of those codecs to play videos you should do:
```
sudo apt-get install libdvdcss2 w32codecs
```

when I get home I will find out the proper commands to download all plugins you need to watch regular videos.

Good Luck

-LuisGMarine

---

### Post by Najand on 2007-04-30
Why don't you switch back to intel drivers then?

---

### Post by ivik on 2007-04-30
Are you using beryl or compiz? It happened in gentoo to, with 2.0 intel driver and xorg 1.3 i cant play movies with xv as output, but they play fine with gl as output. This is with all players:mplayer,xine,vlc.
With 1.7.4 they play fine.

---

### Post by Billy McCann on 2007-05-01
hi everyone.  The responses are much appreciated.

[QUOTE=LuisGMarine]Have you installed any of the codecs?[/QUOTE]

yes.  They're all installed.

[quote=najand]Why don't you switch back to intel drivers then?[/quote]
I may switch back.  The screen is a lot clearer and the monitor's best resolution is available when I use this driver, though, so I'd like to find a solution instead of simply throwing my hands in the air and switching back to the inferior driver.

[quote=ivik]Are you using beryl or compiz?[/quote]
yes. And the video played fine before i switched from the i810 to the Intel driver.

[quote=ivik]It happened in gentoo to, with 2.0 intel driver and xorg 1.3 i cant play movies with xv as output, but they play fine with gl as output. This is with all players:mplayer,xine,vlc.
With 1.7.4 they play fine.[/quote]
Still cannot play.  

When I open vlc and try to browse my files to open one, I get the following error in the terminal:  

```
(.:13204): Gtk-CRITICAL **: gtk_propagate_event: assertion `GTK_IS_WIDGET (widget)' failed
```

And, of course, if I try to play a .mpg by double-clicking it, it automatically crashes, still. 


Thanks for your responses.  


Billy

---

### Post by honghai on 2007-05-08
Hi Billy, I have the identical problem with my 915 intel card. You can use the new version of intel driver and the xorg from debian repository:

[http://packages.debian.org/unstable/x11/xserver-xorg-video-intel](http://packages.debian.org/unstable/x11/xserver-xorg-video-intel)
[http://packages.debian.org/unstable/x11/xserver-xorg-core](http://packages.debian.org/unstable/x11/xserver-xorg-core)

You can follow the links to download the packages, and install the two packages manually. I didn't figure out how to use the debian repository in sources.list.

It does the work perfectly.

---

