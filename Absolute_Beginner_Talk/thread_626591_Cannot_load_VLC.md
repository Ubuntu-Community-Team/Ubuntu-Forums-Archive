---
title: "Cannot load VLC"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by akparker on 2007-11-29
My laptop is an Acer Aspire 5002Mi ( AMD64, 512MB, DVD+R / DVD+/-RW )

I'm running Gutsy, but I'm brand new to Ubuntu and to Linux in general.

My Totem movie player (v2.20 using GStreamer 0.10.14 and GNOME) will not play commercial or homegrown DVDs.

So, I'd like to install VLC.  I'd especially like to play commercial DVDs

When I try to do this, however, I get the following error message:
[I]Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/I]

I cannot figure out what to do in synaptic to resolve these conflicts.

What additional information do I need to provide for some help?

Being so new, I'm afraid I'll need step-by-step instructions.

Thanks,
Keith

P.S. I'm encouraging coworkers/friends to switch to Ubuntu; so far, I'm very impressed.  But the lack of ease of getting a DVD player working will be a major roadblock for many.

---

### Post by fineas on 2007-11-29
Go to system>administration> synaptic package manager and try to install vlc from there.

---

### Post by chemtut on 2007-11-29
Where are you trying to install from?
Go to synaptic package manager in system >.administration
search for vlc and and download from there-----include plugins

---

### Post by akparker on 2007-11-29
I get the following output from Synaptic when I attempt to load VLC:

[I]bongo:
 Depends: emacs21 or
	emacs22 or
	emacs-snapshot or
	emacsen

libvcdinfo-dev:
 Depends: libcdio-dev  but it is not installable
 Depends: libiso9660-dev but it is not going to be installed

mozilla-plugin-vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: vlc but it is not going to be installed

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

vlc-nox:
 Depends: libavcodec1d but it is not going to be installed
 Depends: libavformat1d but it is not going to be installed
 Depends: libdc1394-13  but it is not installable
 Depends: libgsm1 (>=1.0.10) but it is not installable
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
 Depends: libmpcdec3  but it is not installable

vlc-plugin-alsa:
 Depends: vlc but it is not going to be installed

vlc-plugin-arts:
 Depends: vlc-nox but it is not going to be installed
 Depends: libartsc0 (>=1.5.0-1) but it is not installable

vlc-plugin-esd:
 Depends: vlc-nox but it is not going to be installed

vlc-plugin-ggi:
 Depends: vlc-nox but it is not going to be installed

vlc-plugin-glide:
 Depends: vlc-nox but it is not going to be installed

vlc-plugin-sdl:
 Depends: vlc-nox but it is not going to be installed

vlc-plugin-svgalib:
 Depends: vlc-nox but it is not going to be installed

wxvlc:
 Depends: vlc but it is not going to be installed[/I]


Thanks,
Keith

---

### Post by fineas on 2007-11-29
In synaptic package manager 's bar menu, go to settings>repositories. In the first tab, make sure that main, universe, restricted and multiverse are ticked. Then, click the update butoon down the menu bar and retry install vlc (and plugins).

---

### Post by chemtut on 2007-11-29
if no success with the repos.,try mplayer
good luck

---

### Post by akparker on 2007-11-29
Will try both options when I get back home ... not in front of my Linux PC right now.

Will mplayer play DVDs?

I thought it was audio/music player?

Thanks for your patience with me.

Keith

---

### Post by akparker on 2007-11-29
> **fineas said:**
> In synaptic package manager 's bar menu, go to settings>repositories. In the first tab, make sure that main, universe, restricted and multiverse are ticked. Then, click the update butoon down the menu bar and retry install vlc (and plugins).

This process worked!

Activating main, universe, restricted & multiverse seems to have been the key.

The problem appears to be solved.

Thank you both for your help.

Keith

---

### Post by uncurled on 2008-04-19
Thanks! This thread solved my problem, too.

---

