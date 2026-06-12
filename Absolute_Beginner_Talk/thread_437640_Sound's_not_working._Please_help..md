---
title: "Sound's not working. Please help."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-05-09
Ever since I've been messing with the sound to get it to work for flash on Firefox, it's been... well, not working. The first time I did it, it worked, but after shutting it down for the night and starting it up again the next day, it decided not to.

I've done what's written [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox), but that doesn't seem to help.

Anyone?

---

### Post by MockY on 2007-05-09
Does the sound work fine otherwise?

---

### Post by Dysan on 2007-05-09
No, it doesn't. I don't hear any login or logout sounds and when I try to test my sound it just stays at "Testing..."

---

### Post by MockY on 2007-05-09
What sound card do you have.

For Intel HDA cards, I have been successful using this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

For general sound issues, I have been successful using this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Dysan on 2007-05-09
Not sure what HDA is, but it's a Creative Sound Blaster Audigy SE. I'll try the general issues link.

---

### Post by NeoLithium on 2007-05-09
Sometimes it might be something simple as well (I know that mine for some reason reset my volumes on a shutdown and I had to turn them up again just one time)  Try opening up a terminal window and typing:
alsamixer

Turn all the volumes up and make sure nothing is muted...

---

### Post by Dysan on 2007-05-09
The HDA thing doesn't seem to apply to me and the other thread didn't help. All my sounds are up, according to alsamixer too.

---

### Post by MockY on 2007-05-09
Try this. Open terminal and type/paste this into it:

> 
sudo aptitude reinstall linux-sound-base alsa-base alsa-utils



---

### Post by Dysan on 2007-05-09
Nothing. :/

---

### Post by MockY on 2007-05-09
Make sure to reboot afterwards

---

### Post by Dysan on 2007-05-09
> **MockY said:**
> Make sure to reboot afterwards
Wow, awesome. That worked, lol. Thanks a lot. :D

---

### Post by MockY on 2007-05-09
No problem. Glad I could help.

---

