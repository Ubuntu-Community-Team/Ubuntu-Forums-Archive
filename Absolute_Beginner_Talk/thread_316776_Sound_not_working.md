---
title: "Sound not working"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by myslin on 2006-12-11
After installing Ubuntu the sound worked right out of the box but after some package installations (none related to sound) and a restart the sound stopped working, I checked the mixer settings and they seem to be fine, when an mp3 is opened up there is no error message and it looks like the sound is getting processed, its just not coming out of my speakers. I'm using an M-Audio Revolution 7.1 Soundcard. Any help would be appreciated. Thank you in advance.

---

### Post by wpshooter on 2006-12-11
Are system sounds working ?

You say some package installations.  How did you install these ?  Did you install thru Synaptic ?  Or did you install via either the command line or thru Automatix ?  If via the latter two, that would be my **guess** as to the problem.

---

### Post by myslin on 2006-12-11
not getting any system sounds either, Installed them through automatix. I'll go ahead and try to uninstall all the packages right now.
EDIT: Nope, did not fix the problem

---

### Post by rajeev1204 on 2006-12-11
hi

had a similar problem. 

and a really silly reason.

when i had multiple applications like gxine and rythmbox running , adjusting volume on one changed the volume for everything else also

and one time gxine had sound on mute !!i changed that and got sound back

so try opening all multimedia apps and try adjusting volume conrol

iam not sure this is your problem, but if it was then glad to help


regards

rajeev

---

### Post by myslin on 2006-12-11
that did not work either with only 2 multimedia apps installed both had high volume.

---

### Post by Famicommie on 2006-12-11
I had a soundcard issue for a little while, too. When you right click on your volume control and select preferences, what device/drivers does it list?

---

### Post by myslin on 2006-12-11
Devices 
Default
#0 HDA Intel
#1: M Audio Revolution-7.1 <- Selected
Wannabe Master: PCM,0

---

### Post by highneko on 2006-12-11
Sometimes the sound gets turned down all the way when you mute, could this be the problem? Make sure your speakers are powered on and the wires are connected properly.

Here's something I found on google when searching for a ubuntu sound test:
[http://ubuntuforums.org/showthread.php?t=29815](http://ubuntuforums.org/showthread.php?t=29815)

---

### Post by myslin on 2006-12-11
I'm sure that its not muted, Just checked and the wires and speakers are powered on and as I said, it worked before I restarted the system.

---

### Post by arnieboy on 2006-12-11
go to **gnome volume control** and unmute your volume from there if its muted.

---

### Post by Famicommie on 2006-12-11
Two things: 

1. Try the other devices. For the longest time I couldn't get sound when I had my Audigy 2 selected as the device, but when I switched to my onboard NVidia CK8S there was no problem. (It does work through the Audigy 2, now)

2. What exactly did you install before you rebooted? Even though you say it wasn't sound related, it might still be helpful to review the packages you installed to verify what might've changed your sound config.

---

### Post by myslin on 2006-12-11
I just switched the Device to my onboard intel audio and plugged the speakers in, its working now so I'm guessing that its a card/driver issue that i'd still like to resolve.

EDIT: Azureus, Xchat, Swiftfox + Plugins, GFTP, Gnucash, Google Earth, Gaim and Gmail Checker were installed.

---

### Post by nrgtek on 2006-12-11
No sound here either, on my Intel integrated soundboard. I installed a few apps like Xchat and bluefish. 

This was after a fresh install of 6.10. Nothing muted, tried other devices listed with no luck.

---

### Post by P235 on 2006-12-11
This is probably a silly suggestion at this point, but have you tried jiggling the volume for master and pcm under the alsa mixer?  Works for me :/

---

