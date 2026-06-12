---
title: "Can't Play DVD's"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-11-27
Hi,

I'm trying to play a DVD in Totem but it says I don't have the necessary plugins. I've searched for any related plugins in Synaptic but I can't find anything. Any suggestions?

---

### Post by taurus on 2007-11-27
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by philinux on 2007-11-27
Read this sticky too.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by CosmicFlux on 2007-11-27
OK, so I've installed GXine and the related plugins but I'm still having the same problem. It says the DVD can't be read. I've tried three different players and still nothing. In the Mplayer the DVD plays but there is no video, only audio. I'm confused...Totem still says the DVD is encrypted and suggests I install libdvdcss...which I've done.

---

### Post by Chainer on 2007-11-27
I am constantly getting the same issue as well.  Basically I get past the DVD menu and to the FBI warning...once I get to the FBI warning, I get the encryption error telling me that I need to install libdvdcss.

So, any help on this would be great!

---

### Post by philinux on 2007-11-27
Open System>admin>synaptic package manger search for libdvdcss click the checkbox to mark it for installation then click apply in the top menu bar.

You will be prompted for your password.

---

### Post by BrettA on 2007-11-27
I'm no expert, but I managed to get DVDs working by downloading/installing Automatix.
It then asked me what I wanted to install, along with a few other things I chose DVD decoder & now it just works. Simple as that.

---

### Post by philinux on 2007-11-27
Just be aware automatix is not supported by ubuntu.

Some people have had no probs others have reported it broke there system.

---

### Post by houstonbofh on 2007-11-27
First, check out ogle-gui as it is a much nicer player.  If you have libdvdcss and ubuntu-restricted-extras installed, and ogle still fails, post back.  That combination has worked for me on every system I have tried.

---

### Post by jstableford on 2007-11-27
> **Chainer said:**
> I am constantly getting the same issue as well.  Basically I get past the DVD menu and to the FBI warning...once I get to the FBI warning, I get the encryption error telling me that I need to install libdvdcss.

So, any help on this would be great!

I just followed the instructions on the link provided by another user:

 
 [B][I]     Ubuntu 7.10 "Gutsy Gibbon"

In gutsy to get encrypted DVD playback to work i had to do the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh[/I][/B]
 
I then installed **gxine**, and am able to watch DVDs.

Best of luck

---

### Post by stchman on 2007-11-27
> **CosmicFlux said:**
> Hi,

I'm trying to play a DVD in Totem but it says I don't have the necessary plugins. I've searched for any related plugins in Synaptic but I can't find anything. Any suggestions?

I have never had much luck with Totem and DVD playing.  For DVD playback I use VLC.

---

### Post by ronmarley1 on 2007-11-27
> **stchman said:**
> I have never had much luck with Totem and DVD playing.  For DVD playback I use VLC.

+1

---

### Post by Chainer on 2007-11-27
I have tried all of that stuff...I already have libdvdcss installed...what I was reiterating on, was exactly what the previous poster had said.  DVDs will start playing, then we get the error message saying that libdvdcss is not installed (although it is).

---

### Post by stchman on 2007-11-27
Follow my procedure to get encrypted DVD playback.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

