---
title: "Problems with Mplayer"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by shawn.mnb on 2008-01-03
Hi, Im having some problems installing mplayer properly on my system. I thought I had it installed correctly, but when I go to apple.com/trailers, all trailers show up as a grey screen with the mplayer logo in the background. It then tells me it is buffering and sound will play, but no video. When I try to open up the mplayer application itself it says 
[skin] error in skin config file on line 24: PNG read error (/usr/share/mplayer/skins/default/font)
[skin] error in skin config file on line 24: Font image file not found.

Ive tried reinstalling a few times but to no avail. It seems the other plugins buffer too slowly and have jerky movement so Id like to try this one - I hear its the best.

in terminal when I type 'gmplayer' I get:

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] error in skin config file on line 24: PNG read error (/usr/share/mplayer/skins/default/font)
[skin] error in skin config file on line 24: Font image file not found.
skin config file read error (default)

any suggestions?
please help!

---

### Post by ~LoKe on 2008-01-03
You have mplayer installed, but do you have codecs to play the video?

---

### Post by philinux on 2008-01-03
I would try this.

Close mplayer. Goto your home folder. Ctrl H to see hidden folders locate .mplayer and delete it.

Thats mplayers config file. Restart mplayer and it will generate a new one.

---

### Post by shawn.mnb on 2008-01-04
hey

I tried your idea of deleting the .mplayer folder and originally it didnt work. What I ended up doing was  uninstalling mplayer via automatix and then going into synaptix to make sure that all aspect of the program were deleted [which they weren't]. then i went in and deleted the .mplayer folder and went back into synaptix and reinstalled. voila it worked. thanks for your help.

---

