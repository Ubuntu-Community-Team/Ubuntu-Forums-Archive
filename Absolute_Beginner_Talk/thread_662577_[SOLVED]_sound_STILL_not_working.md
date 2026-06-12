---
title: "[SOLVED] sound STILL not working"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by winsall on 2008-01-09
hey, ive tried nearly everything in the comprehensive sound problem solution guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)).

aplay -l reveals
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

however,in the volume mixer, it has realtek alc883 as an option (has the same model number as first intel in aplay) so im not sure if it means anything.

nothing is muted, so im just not sure.

any ideas?

thanks in advance,
winsall

P.S i ran sudo /etc/init.d/alsa-utils stop   and   sudo /etc/init.d/alsa-utils start
however this didnt work.

---

### Post by Pevichaey5 on 2008-01-09
has your sound ever worked like when running the live cd?

---

### Post by balaknair on 2008-01-09
Hi
have you tried the hda-intel how to at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

if not I'll just outline a few key steps from it which I think will solve your problem

In a terminal type this command
```
cat /proc/asound/card0/codec#* | grep Codec
```
This will tell you what codec your card uses

Next open this link [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
and find your version on it(I've done it assuming the codec you need is ALC883, but you can check with the above command just to be sure)
eg: For ALC883 in the config file in the link above
ALC883/888
851		  3stack-dig	3-jack with SPDIF I/O
852		  6stack-dig	6-jack digital with SPDIF I/O
853		  3stack-6ch    3-jack 6-channel
854		  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
855		  6stack-dig-demo  6-jack digital for Intel demo board
856		  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
857		  medion	Medion Laptops
858		  medion-md2	Medion MD2
859		  targa-dig	Targa/MSI
860		  targa-2ch-dig	Targs/MSI with 2-channel
861		  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
862		  lenovo-101e	Lenovo 101E
863		  lenovo-nb0763	Lenovo NB0763
864		  lenovo-ms7195-dig Lenovo MS7195
865		  6stack-hp	HP machines with 6stack (Nettle boards)
866		  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
867		  auto		auto-config reading BIOS (default)

find the description which best matches your system's sound setup.

Then in a terminal type
```
sudo nano /etc/modprobe.d/alsa-base
```

Move to the end of the file(use down arrow to scroll down) and paste this line as the last line
```
options snd-hda-intel model=MODEL
```

replace MODEL with your model from the alsa-conguration page(eg a 5.1 sound system with 3 audio jacks would be a 3stack-6ch)

Reboot

This usually fixes the problem in most cases.
For further options, take a look at the  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) page

---

### Post by balaknair on 2008-01-09
PS please reply and let me know the outcome
if it works you might also mark the thread as solved

---

### Post by winsall on 2008-01-09
im giving it all a shot, ill let you know how it goes when im done

@thexero:
it worked when i had fiesty

---

### Post by winsall on 2008-01-09
OMG OMG OMG OMG i get sound through my headphones, but not my speakers

SOOOOOOOO CLOSE!!!!

someone please help me finish this off!!!

---

### Post by philinux on 2008-01-09
> **winsall said:**
> OMG OMG OMG OMG i get sound through my headphones, but not my speakers

SOOOOOOOO CLOSE!!!!

someone please help me finish this off!!!

If i have my headphones plugged in they mute the speakers on my system.

---

### Post by kpkeerthi on 2008-01-09
Type **alsamixer** in a terminal and make sure **PCM** slider is raised enough. Press 'Esc' to save and quit from alsamixer.

---

### Post by winsall on 2008-01-09
@philinux:

yeah i know but when they arent plugged in = nothing when they are = sound! :)

@kpkeerthi:

no such luck. PCM is already at full volume

---

### Post by philinux on 2008-01-09
> **winsall said:**
> @philinux:

yeah i know but when they arent plugged in = nothing when they are = sound! :)

@kpkeerthi:

no such luck. PCM is already at full volume

Glad you've got progress. Even with headphones is a start.

It sounds like something is muted somewhere. I would install gnome-alsa-mixer and run it. It's a nice gui and alot easier than the cli alsamixer. 

Good luck I'm sure you'll crack it.

---

### Post by winsall on 2008-01-09
i installed gnome alsamixer, but i dunno where to find it. maybe its just coz im stupid :P

---

### Post by philinux on 2008-01-09
> **winsall said:**
> i installed gnome alsamixer, but i dunno where to find it. maybe its just coz im stupid :P


If you installed **gnome-alsamixer** it puts a menu entry under Applications>Sound & Video

---

### Post by winsall on 2008-01-11
i figure headphones is enough, worst comes to worst, ill get some el cheapo speakers from work. thread SOLVED :) thanks for all the help!

---

### Post by rkd on 2008-01-12
I hate to see you settle for only headphone output.

Did you try all the model numbers for ALC883 devices indicated in the howto that balaknair pointed to in post #3? I know there are a lot of them to try, but we might be able to get lucky by picking the ones for computers that seem close to yours.

If you are just tired of fighting with it and want to drop it, that's okay. Your choice. But if you'd like to try a little more, I'm willing to try to help. (I don't have any special knowledge of the sound software. So I can't guarantee my ideas will be any better than guessing.)

---

### Post by vervelover on 2008-01-15
Hi, I'm in the same situation of winsall, only headphone out works, and only at a really low volume, I have a Medion RIM 2150 laptop, I tried all options for my Realtek Alc880 but none seem to work.It's got 2 jacks on the back, one in and one out, and 1 s-pdif digital out on the side. The strange thing is I can't mute/unmute pcm on alsamixer, it seems to be set on the max volume but no turning on/off..

---

