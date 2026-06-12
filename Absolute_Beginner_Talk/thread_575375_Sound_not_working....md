---
title: "Sound not working..."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Gdobbs on 2007-10-14
Hello all, I have installed Ubuntu 7.04, and can't get the sound to work. I have tried MANY "fixes" and still no results. Any and all help apreciated. Please note: I am a new Linux user, please talk to me as if I were a 3 year old. Thanks.

ps. I am using the onboard audio (Realtek audio)

---

### Post by jaygo on 2007-10-14
hrmmm, let's get some more details. What's your computer or motherboard model? And what type of audio cables are you using to connect with? For that matter, are you connecting to the back of the PC & have you tested for sound with other sets of speakers or headphones?

---

### Post by Gdobbs on 2007-10-14
Motherboard:

"Biostar P4M900MICRO775 mATX LGA775 DDR2 VIA P4M900 1PCI-E16 2PCI SATA Video Sound LAN Motherboard"

Audio cables? Im just plugging my headphones into the back (motherboard) of my PC. Linux recognizes the Motherboard as being a soundcard. I have tried different headphones, and the sound/headphones work when I boot in windows. Hopefully that tells you a bit more.

---

### Post by jaygo on 2007-10-15
Great. Yeah that's all I needed. What programs are you using that aren't giving you any sound? Firefox? Rhytmbox? And do you have amarok (music player) installed? I'm most familiar with its audio options.

Something to try now (if you haven't already) ... start up a console (I hate even having to say that) and type alsamixer. It's a graphical/text interface for adjusting your audio devices. 
Use your left & right arrow keys to move and check to see if anything is muted -- you'll see an MM if it's muted. Hit the M key to mute/unmute. Mic is okay to leave muted. More info about[ alsamixer here]("http://alsa.opensrc.org/index.php/Alsamixer").

and check out the following, they might give you a lead:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893/comments/101]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893/comments/101")
[http://ubuntuforums.org/showthread.php?p=3064228]("http://ubuntuforums.org/showthread.php?p=3064228")

---

### Post by Gdobbs on 2007-10-16
Alright, everything seems un-muted.

---

### Post by jaygo on 2007-11-04
Sorry, I missed your reply. Does that mean you got it working?

---

