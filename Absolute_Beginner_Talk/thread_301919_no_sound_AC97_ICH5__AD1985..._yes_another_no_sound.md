---
title: "no sound AC97 ICH5 / AD1985... yes another no sound post... sorry."
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by mahavishnuO on 2006-11-17
Well i've noticed a LOT of people have had sound issues. And i've sifted through tons of posts and cant resolve me sound issue.. which is NO sound.

system>preferences>sound
shows nothing for default sound card and no sound cards show up in the menu.

I have onboard sound, intel motherboard. 

The following code:
```
cat /proc/asound/cards
```

gives me:
```
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with AD1985 at 0xffa00400, irq 
```209

The AC'97 audio controller shows up in device manager.

When i run:
```
sudo gedit /etc/modprobe.d/alsa-base
```

OUTPUT:

```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

Im a noob, i've tried a lot of things that i've found in other posts. Im using dapper drake kernel 2.6.15-27-386

ummm. what else can i tell you. when im logging in, if i enter an incorrect password, i can hear a little sound blurb play. but then nothing after that once im logged in.

help! **i'm starting to think maybe i'm deaf!?**

---

### Post by mahavishnuO on 2006-11-18
](*,) anyone?

---

### Post by devnu11 on 2006-11-21
I am having basically the same problem with edgy and it is difficult to describe.  I have sound if I play a mp3 or video.  I also have sound when i log in and out.  Once I'm logged in the sound stops unless I activate something manually.  Once and a while I will get a sound from amsn if someone logs in but it is rare.  Usually amsn is silent along with all the other programs.  
My VMware Server can not connect to sound on localhost via the viewer.  I though it was a permissions problem but temp making everything writable and adding to groups had no effect.  The message from vmware is something like can not connect to /dev/dsp its busy or not available.  Is there some sort of loader config in linux as there is in FBSD?

$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at 0xffa80400, irq 201

---

### Post by randytuggle on 2006-11-22
I'm a noob also (about 2 weeks into this linux/ubuntu gig) - but I have a tip on the VMWare Server issue. When using VMWare server, sound will not work IF you are currently using your sound card to play music or movies while running desktops on Ubuntu. In order to get sound through VMWare , you must have your  guest OS powered off - then use VMTools to add sound. If you add sound before starting the OS in VMWare, you should be ok from that point. Just remember that you cannot share your sound card with an Ubuntu app while running VMWare server. 

Now I have a sound card issue that I need to fix as well... whenever I change the system preferences>sound menu to USE MY actual soundcard, I cannot play music through Streamplayer. However, if I set the sound preferences to use generic crap - THEN my Audacity program works fine. One way or the other, I lose sound across the Ubuntu OS. Any tips on how to remedy this issue?

---

### Post by Sef on 2006-12-03
This is how I got mine to work:

Commented out the penultimate line and changed the last line from 2 to 0.

>  # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
# options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0


---

### Post by randytuggle on 2006-12-03
> **Sef said:**
> This is how I got mine to work:

Commented out the penultimate line and changed the last line from 2 to 0.
Thanks for the tip - but which file am I supposed to alter with those lines? Forgive my stupidity..

---

### Post by Sef on 2006-12-03
> Thanks for the tip - but which file am I supposed to alter with those lines?

Applications > Accessories > Terminal

```
sudo gedit /etc/modprobe.d/alsa-base
```

> Forgive my stupidity..

Not stupid.  You asked, so you could learn and that is never stupid.

---

### Post by carusoswi on 2007-03-24
ok.
When you comment out lines of code, well, how do you do that?  I ran sudo gedit /etc/modprobe.d/alsa-base, and it ran and gave me a bunch of code.  How would I go about altering that code than running it so it has an effect on my setup?

I have the AC97, and since installing ubuntu 6.10, that card has been out of service.  I even installed XP and could not get it to work.

Prior to fiddling around with ubuntu, I had a two-sound-card system, the AC97 integrated card and my PCI add-in Audigy LS.

I could select between them, record through the Audigy, playback through the AC97, etc.  If I install the Audigy, ubuntu will use it without any action on my part.  The AC97 will not work no matter what I do.

Right now, I have pulled the Audigy out of the system in an attempt to discover what the problem is with the AC97.

Any advice welcome.

Caruso

---

### Post by sundial on 2007-03-24
I am new to the Linux world and just set up Ubuntu 6.10 on a spare PC.  The MB is Intel, the CPU is Intel Pent 2ghz.  The MB has a sound component called AC97 and the board has a separate card for sound called a Ensoniq ES 1370 PCI card. 
I tried to set up the sound on both the built in controller and the card.  I removed the card and tried the built in chip all attempts lead to nothing.  No sound, not even static from the speakers.
Earlier I tried installing the earlier version of this OS 6.06 and same thing, no sound, so I installed the 6.10 and also, no sound.  In all cases I used the sound set up "Sound Preferences" 
Any thoughts and suggestions would be appreciated.

Sundial

---

### Post by pureblood on 2007-04-10
This workaround might work but it is not a solution:
[http://ubuntuforums.org/showthread.php?p=2430827#post2430827](http://ubuntuforums.org/showthread.php?p=2430827#post2430827)

---

### Post by hockey97 on 2007-04-10
Hi I am not getting any sound, I have a sound card in my pci slot I got a  Sound BLaster live 8 channel card pci  and have a thunderbird AMD 900megahertz processor, I am not sure where to get drives for it in linux, I am using ubuntu6.10 server and desktop.  I  Need to know what I need to get my sound card working the driver cd that came with it was for only windows OS.  I am not sure if the sound card supposed to say if the card is linux capadable??

I am a noob at linux just really only got 4 months under my belt of ubuntu linux stuff.

also just done a check in ubuntu to see if card is detected and got this result...

# cat /proc/asound/cards
 0 [rev20          ]: VIA686A - VIA 82C686A/B rev20
                      VIA 82C686A/B rev20 with STAC9721,23 at 0xcc00, irq 5
 1 [Live           ]: EMU10K1 - SBLive! Value [CT4831]
                      SBLive! Value [CT4831] (rev.7, serial:0x80311102) at 0xe000, irq 10

Don't know what it means really.

---

