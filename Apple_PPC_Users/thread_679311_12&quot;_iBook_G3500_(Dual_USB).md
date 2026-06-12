---
title: "12&quot; iBook G3/500 (Dual USB)"
date: 2008-01-26
forum: Apple PPC Users
---

### Post by Ripfox on 2008-01-26
I have absolutely no video playback with this at all. I have successfully installed 7.04 through the alternate install cd, fixed the resolution problems, got streamtuner workin' fine, email, but vlc or ANY other media player just crashes when I try to play video files. It doesn't matter what kind, .flv, wmv, .mov or whatever. I also get no playback in a mozilla bowser. Mplayer loads to 8% and freezes (no controls either) I have followed the wiki and installed all the ppc codecs also I switched between the totem/gstreamer plugin, the mplayer plugin and the vlc embedded plugin to no avail. when I download a clip as suggested to open it with vlc, it hangs for a second then crashes. I also went to synaptic and installed alll th gstreamer plugins I could find and even tried "ubuntu restricted extras"


WHEW

Whats the dealio??  :confused:

---

### Post by Ripfox on 2008-01-26
bump

---

### Post by stream303 on 2008-01-27
I took a look at your model on

[http://www.everymac.com](http://www.everymac.com)

and saw that it comes with 64 or 128mb standard.  Were you able to play movies with OS9?

It may not be the source of your problems, but I'd be interested in running top, or better yet, HTOP (synaptic download and install) in a terminal while you launch these apps.  If running plain Ubuntu, maybe add the system monitor to the top panel and have it show memory as well as cpu and bring those apps up.

just a shot..

---

### Post by ssam on 2008-01-27
does audio work?

can you play the 'ubuntu sax.ogg' file that comes in the examples folder in your home folder

---

### Post by Ripfox on 2008-01-27
Audio works after adding a module (snd-powermac)?

can't remember. But yea.

I have 320 mb ram, so I doubt this to be the issue.

Any other ideas? Why does the mplayer plugin buffer up then die?

---

### Post by Ripfox on 2008-01-27
Here is a screenshot...

---

### Post by Ripfox on 2008-01-27
PLEEEASE someone help me get to the bottom of this...I have a near perfect install on a mac and it would be awesome  to be able to play embedded (or ANY) movie files...:(

---

### Post by stream303 on 2008-01-28
I was looking at the FAQ for something else and saw that when you install the firefox mplayer plugin, you should remove totem mozilla plugin.  Could this be the source of conflict?

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by Ripfox on 2008-01-28
Unfortunately, this is not the problem. I was aware of that issue and followed those instructions. :( I even went into the mozilla-firefox folder and removed all instances of totem from the plugins folder...

Anybody else?

---

