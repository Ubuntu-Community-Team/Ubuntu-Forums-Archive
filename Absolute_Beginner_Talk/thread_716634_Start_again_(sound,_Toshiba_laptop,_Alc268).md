---
title: "Start again (sound, Toshiba laptop, Alc268)"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-03-06
In an hour I`m going to do a fresh 7.10 install on a Toshiba laptop. The laptop has no sound. It has a Alc268 soundcard and I haven`t managed to get it working.  I reckon I`ve looked at every related thread  on this forum and plenty of others too.
 I`ve tried so many ways of fixing this I`m not sure where I`m up to. My desktop is almost full of tar files.
  My fear is that something I have tried may be the solution but because I`ve altered my system so much  it doesn`t work. 
  Has anyone come up with a definate way to fix this problem on this laptop so I can install, fix it and go.
The in built wireless doesn`t work either btw but I have a usb thingy that does so I`m not worried but a solution would be nice.

---

### Post by lswest on 2008-03-06
well, what wireless card is it?  could you post the output of ```
lspci
ifconfig
iwconfig
``` it would help us help you ^^ and i'm sorry, but i have no experience with sound issues
(run each line as a seperate command in a terminal)

---

### Post by Arthur Archnix on 2008-03-06
Since you've tried it all my suggestion is to do a clean install, upgrade the packages, then build and install the latest version of alsa.

Good luck.

---

### Post by nothingspecial on 2008-03-06
The card is an alc268 hda intell. I can`t run the codes yet cause I`m installing. Thanks

---

### Post by nothingspecial on 2008-03-06
Ok, brand new 7.10 instalation.  Sound icon is muted, nothing I can do to change it. Alsamixer gives me 2 options "caller i" and "off-hook". I can mute + unmute them but I can`t raise the volume.
aplay -l gives me
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
From memory I have to do something about generic-modules to find the card.???????

---

### Post by nothingspecial on 2008-03-06
Got generic- backports. Compiled alsa .16. Added lines to alsa-base. NOTHING. Shall I just give up? It`s been over 4 weeks now.

---

### Post by nothingspecial on 2008-03-06
I`m so frustrated. I have a pc that runs Ubuntu perfectly. I have a sony laptop that also runs Ubuntu great( no webcam but I`m not bothered). My brother has my sony laptop because I persuaded him to install Ubuntu on this. WHY DOES UBUNTU HATE TOSHIBA SO MUCH?????????

---

