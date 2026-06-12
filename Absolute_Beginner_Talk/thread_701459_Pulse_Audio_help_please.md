---
title: "Pulse Audio help please"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Rezistik on 2008-02-19
I tried the Fedora Live CD before installing ubuntu and would like to have the same per application audio style as Fedora, I have installed all the Pulse Audio packages from synaptic but it says server denied....which makes me wonder why it has to connect to a server...anyways, does anyone have any ideas on getting the per application sound levels to work?

Thanks in advance :D.

---

### Post by sabatron on 2008-02-19
I don't know anything about audio, but try posting this in the Multimedia and Video section for a faster reply.

[http://ubuntuforums.org/forumdisplay.php?f=138]("http://ubuntuforums.org/forumdisplay.php?f=138")

---

### Post by Rezistik on 2008-02-19
I would hate to like post the same thing in too many places, could a Mod move this if it is in the wrong place?


Please and thank you. :D

---

### Post by Rezistik on 2008-02-19
Help...

---

### Post by oni5115 on 2008-02-20
Did you use the Synaptic Package Manager, or the Add/Remove menu?

If you used the latter, make sure you also got the compatibility file.  If you use SPM it should come up as "pulseaudio-esound-compat".  WARNING: installing this will remove elightened sound daemon and replace it with Pulse Audio.

Note:  If Wine is more important that PA, don't bother with it (yet).  The versions in the repo, 0.96,  seem to not work with wine 9.54.  Someone else had it working, but they had downloaded and compiled the 0.97 version of PA, because the 0.96 versions didn't work for their hardware, and that seemed to work with Wine.  Just thought I'd mention it, since the only reason I really wanted the multi-program volume control was Ventrilo.  =/

---

### Post by Rezistik on 2008-02-20
I used the add/remove menu...I thought it was synatic....

---

### Post by oni5115 on 2008-02-20
I'm referring to the System > Administration > Synaptic Package Manager

It lets you specify exact packages for install, I noticed quite a few 'extra' type of features get missed with the Add/Remove window.  For instance, most media players skip the firefox plug-ins ... would be nice it it auto installed those if you had firefox installed, but that is beside the point.  I'm guessing if you used the Add/Remove window that it didn't install the the "pulseaudio-esound-compat" package which actually makes PulseAudio run instead of ESD.

I've got it working with Wine now too, despite the error messages I got I just had to switch it to ESD instead of ALSA and it works now.

---

