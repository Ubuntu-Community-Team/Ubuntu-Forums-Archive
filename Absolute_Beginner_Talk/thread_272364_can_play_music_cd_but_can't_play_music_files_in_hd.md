---
title: "can play music cd but can't play music files in hdd"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2006-10-06
hi all ,
when boot i can hear sound , both sound when i type password and sound when ubuntu load and ofcourse when i shutdown comp . i also can hear sound from cd music . but i really can't understand why i can't hear sound from music files .
in sound manger i saw that there're 3 devices : i used  file -> change device -> 0: HDA ATI SB (Alxar Mixer) - 1: Dell Sound blaster live (Alxar Mixer) - 2: Realtek ALC883 (OSS Mixer) . And I choose Realtek .
i installed juK , Noatun and amaroK but both of them didnt work . with juK and amaroK , i opened some files but they couldnt play . with Noatun , when it started it warned me : "Connecting/starting aRTs sound server failed . Make sure that artd is configured properly ."

pls help me fix this bug , i asked people in ubuntu irc chat but didnt receive solutions .
thanx for all ur helps .

---

### Post by pstewart on 2006-10-06
It sounds like you're trying to play music files in restricted formats (eg. mp3). Due to licensing issues mp3 isn't supported out of the box, but it's a fairly easy fix.

This link should provide some help [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Hope that helps,
Pete

---

### Post by Malta paul on 2006-10-06
I agree with Pstewart about restricted formats. If you get the restricted codecs you can just about play any format from your HD. You can use Automatix to download AUD-DVD Codecs and Easyubuntu to down load W32 codecs.
I use VLC Media player, Beep media player , Helix player and Rhythmbox.
These  will not play .MID files but Gnome Timidity++  will. Hope this is of some help. Paul   :)

---

### Post by Aberrix on 2006-10-06
just use automatix ([link]("http://www.getautomatix.com/")) to install the 'restricted file format' extensions, its super easy.

---

### Post by ghostshadow189 on 2006-10-06
hi , i installed automatix to install w32codecs and others that support media . but i still can't listen to .mp3 files , i just can play .ogg files .
i think maybe my prob is that :
> in sound manger i saw that there're 3 devices : i used file -> change device -> 0: HDA ATI SB (Alxar Mixer) - 1: Dell Sound blaster live (Alxar Mixer) - 2: Realtek ALC883 (OSS Mixer) . And I choose Realtek .
pls help me to listen mp3s . thanx so much .

---

### Post by motstudios on 2006-10-07
id suggest (mainly from my own preference) that you get xmms installed to play mp3. in the xmms preferences u can choose which soundcard (if you have multiple ones) and choose software mixer and alsa.

xmms has never given me any problems. its not as pretty as say beep media player or amarok but it works and to me i like things that "just work"

u can try searching for xmms in synaptic, u may have to enable multiverse and universe in the repository options (edit the main repository).

if you have already installed the w32codecs and u can hear other sounds, then ur soundcard is working, just need an audio player that plays the mp3.

NOTE: id suggest the use of ogg before mp3. mp3 may be popular but ogg is awesome. anytime you rip songs from a cd, encode to ogg.

---

### Post by jaboua on 2006-10-07
Also try choosing something else than the realtek. There are two sound systems for linux: ALSA and OSS, OSS being the old standard in linux and is still is used in for example freebsd.

Since not all apps use ALSA, there was created a "OSS Emulation Layer" - so that a fake OSS device (/dev/dsp) should be able to redirect sounds to ALSA. It seems like you have 2 alsa devices, and my guess is that the OSS device is a fake (emulated) device. A possibility is that it doesn't work because of permission errors (in that case try running "sudo chmod 777 /dev/dsp*") or because it redirects sounds to the wrong ALSA device. I would suggest that you first try using what looks like "real" devices though.

---

### Post by ghostshadow189 on 2006-10-07
> **motstudios said:**
> id suggest (mainly from my own preference) that you get xmms installed to play mp3. in the xmms preferences u can choose which soundcard (if you have multiple ones) and choose software mixer and alsa.

xmms has never given me any problems. its not as pretty as say beep media player or amarok but it works and to me i like things that "just work"

u can try searching for xmms in synaptic, u may have to enable multiverse and universe in the repository options (edit the main repository).

if you have already installed the w32codecs and u can hear other sounds, then ur soundcard is working, just need an audio player that plays the mp3.

NOTE: id suggest the use of ogg before mp3. mp3 may be popular but ogg is awesome. anytime you rip songs from a cd, encode to ogg.

thanx so much , i installed xmms and now i can play .mp3 files , but xmms cant play .wma files . so how can i make it play .wma files ?

---

### Post by motstudios on 2006-10-09
theres a wma plugin for xmms... theres a deb package available at this URL:
[http://mark.22kb.com/dl/ubuntu/](http://mark.22kb.com/dl/ubuntu/)

install it with:
sudo dpkg -i /pathtodebfile/xmms-wma_1.0.5-0plf2_i386.deb

---

