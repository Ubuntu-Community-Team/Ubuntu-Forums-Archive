---
title: "Help with sound: YOUTUBE FIREFOX 32-bit"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by lilbrazilianboi on 2007-07-03
Ok. I just installed linux today and I managed to somehow install the sound driver ALSA. When installed the driver i used this website: [COLOR="Red"]https://help.ubuntu.com/community/HdaIntelSoundHowto[/COLOR]
which I probably shouldnt have thinking that my computer is an amd 64 and SATA, but i couldnt find anywhere else to help me install this, it uexpectantly worked though.

[SIZE="3"]After that i began to install the flash player for firefox since i use youtube a lot, but then i noticed that it only works on 32 bit firefox. Learning that i could download a plugin that allowed me to use a 32 bit firefox i went and installed it. Happily video worked perfectly at youtube.com but sadly sound didnt. Now im completely lost. please help![/SIZE]

ps. I also checked at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes](http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes) and said that if sound didnt work at youtube with firefox to go to terminal and type:

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

and

Change:
FIREFOX_DSP="none"
To:
FIREFOX_DSP="aoss"

but i did and it still didnt work.

Please please help! :(

My build precisely being:

Ubuntu 7.04
Amd 64 +3500
A8N-SLI Deluxe Series with a NVIDIA nForce4 chipset (ASUS)
SATA Western Digital 80gb hard drive
1 gb ram

---

### Post by lilbrazilianboi on 2007-07-03
bump

---

### Post by lilbrazilianboi on 2007-07-03
Bump!

---

### Post by Kleber on 2007-07-03
I had the same issue on Gateway Notebook PC (MX6453).
I followed the procedure above and It is working fine now.

Thanks,

Kleber Rodrigo de Carvalho

---

