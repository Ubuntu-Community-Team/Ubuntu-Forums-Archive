---
title: "New soundcard, no sound."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-02-04
Hi

I got a present today, a new soundcard with the name “Sound Blaster X-Fi extreme Fidelity”. You guessed it, the drivers are only for Windows. So it works under Windows, but I have no sound in Ubuntu. 

lspci -v | grep -i audio
The command above gives me this: 

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:02:08.0 Multimedia audio controller: Creative Labs: Unknown device 0005

In System -> Preferences -> Sound I can only choose Nvidia CK8S, not the new one. 


Can you pl help me?

---

### Post by Oki on 2007-02-04
O no... Looks like this card wont wrok with Linux at all; [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix) 

To bad.

---

