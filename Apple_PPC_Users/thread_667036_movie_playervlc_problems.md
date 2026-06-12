---
title: "movie player/vlc problems"
date: 2008-01-13
forum: Apple PPC Users
---

### Post by thespottedelf on 2008-01-13
i have a iMac 500 mhz just shy of a half gig of ram can not play video in vlc or movie player (i installed the codecs)

They open the .avi files but close before they start playing.  Plz help, this was the reason for installing linux on my iMac.

---

### Post by BladeMelbourne on 2008-01-13
I experienced this too (Xubuntu 7.10 user with Radeon 9200).

In VLC preferences, configure to display advanced options.
Find the video output section, and select "X11 video".

The "xv" or "xvideo" option uses a lot less resources, but I found it crashed VLC with some avis (particularly cartoons).

These days, I use VLC with "X11 video" (for cartoons) and Kaffeine with "xvideo" (I got sick of switchiing inside VLC). Kaffeine is growing on me - especially since I can make it buffer more frames without causing delays in pause, etc. controls. The only downside is that it takes longer to start.

Hope this helps.

---

### Post by oswaldkelso on 2008-01-14
> **thespottedelf said:**
> i have a iMac 500 mhz just shy of a half gig of ram can not play video in vlc or movie player (i installed the codecs)

They open the .avi files but close before they start playing.  Plz help, this was the reason for installing linux on my iMac.

I have a imac 333mhz 256mb running debian and it can play video though struggles full screen with some depending on the codecs etc. Your machine should cope so I suspect its your settings. I use mplayer xine and vlc bepending on the file one may work better than another

The things i do to get a better video experience is play in a terminal with mplayer also copy mpeg or avis to the harddisk. some times navigating to the actual  file on a vcd or usb drive works if your player cant find it or fails to play.

You may need to check your source.list include where ever you get you codec (some ubuntu user or searching these forums will help you there)

---

