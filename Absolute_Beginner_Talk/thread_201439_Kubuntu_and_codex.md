---
title: "Kubuntu and codex"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-21
Hi all,

looking for a little advice. I have installed a base version of kubuntu (ie no gnome) i want to set up the codex on my machine so i can watch vids, play music etc. Now the ubuntu guide list the following to be install:

sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install gstreamer0.10-gl
sudo apt-get install gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

my question is will this work if there is no gnome installed on the pc? i was under the impression that "g" in front of a name indicated the requirement of running gnome. If this is the case is there any way to install the codex without installing gnome.

cheers in advance
Niteblind

---

### Post by qamelian on 2006-06-21
No worries. Gstreamer will work with non-Gnome apps as well. Both amaroK and Kaffeine can work with a Gstreamer back-end.

---

### Post by Jucato on 2006-06-21
[QUOTE=qamelian]No worries. Gstreamer will work with non-Gnome apps as well. Both amaroK and Kaffeine can work with a Gstreamer back-end.[/QUOTE]

I don't think so. GStreamer is currently broken/unmaintained in KDE/Kubuntu for now. That's why Kubuntu uses a different method/library for multimedia, Xine.

The instructions for restricted format support in Kubuntu is different from Ubuntu. In Kubuntu, you only need to install 2 packages:

1. libxine-extracodecs - from the multiverse repository. this will handle **everything** (except Windows Media, see #2), all your codec needs, including previewing automatic audio files in Konqueror (the one where you place the mouse over the audio file).
2. w32codecs - the usual stuff. 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There are separate and specific instructions for Ubuntu and Kubuntu.

---

### Post by qamelian on 2006-06-26
I'm using the Gstreamer backend with amaroK right now without any problems. In fact, if I try to use any other backend with the Dapper install on my laptop, amaroK goes nuts and spikes CPU usage at 100%. I find this weird as previously Gstreamer gave me nothing but grief, but at the moment it seems to be my only option.

---

