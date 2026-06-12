---
title: "Another sound card issue"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by nugglets on 2006-05-29
Sorry, I see there are a few other sound card threads with out replies, but none of them are for my sound card so I didnt want to thread jack someone.

Anyways, I have an ATI AC97 sound card that isnt working properly. Checked the alsamixer and all the typical things that every sound thread says to check, but nothing works still. Also tried checking out the alsa site, but i cant even use mkdir and cant get the root account working to save my life so that didnt get very far. Obviously I am a total linux noob, but I would say I am pretty computer saavy in every other respect(programming, hardware, windoze). Please help!

lspci:

> gabis@razorlives:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5951 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:03:07.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


lsmod | grep snd:

> snd_atiixp             18912  1
snd_ac97_codec         72188  1 snd_atiixp
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_atiixp,snd_pcm


Sorry, Im still too newb to decipher what to do from here. Though I can tell that it seems my sound card isnt installed entirely, looks like half the entries are right and half say they arent detecting it. Were this windoze, I would know exactly what to do.. but its not so help meh learn the ways :D Thanks!

---

### Post by jazzmuzik on 2006-05-29
To run a command as root, preceed it with 'sudo' if on the command line, or 'gksudo' if you are running a gui program. If you need to stay in root mode, use 'sudo -s'

Did you click on the speaker icon and see if anything is muted? Did you try System, Preferences, Sound?

---

### Post by nugglets on 2006-05-29
Yea, I checked all the obvious sound configs I could see and nothing is muted and the volume is all proper. Thanks for the gksudo thing, sudo wasnt working for me!

---

### Post by jazzmuzik on 2006-05-30
What's the output when you run this:

```
more /dev/sndstat
```

---

### Post by nugglets on 2006-05-30
gabis@razorlives:~$ more dev/sndstat
dev/sndstat: No such file or directory
gabis@razorlives:~$

Thanks for helping me!:D

edit: ok, now that you showed me how to sudo.. im trying the alsa-project guide again but im getting stuck at " cp /downloads/alsa-* ." its returning "cp: cannot stat `/downloads/alsa-*': No such file or directory"

---

### Post by Sutekh on 2006-05-30
[quote=nugglets]gabis@razorlives:~$ more dev/sndstat
dev/sndstat: No such file or directory
gabis@razorlives:~$

Thanks for helping me!:D

edit: ok, now that you showed me how to sudo.. im trying the alsa-project guide again but im getting stuck at " cp /downloads/alsa-* ." its returning "cp: cannot stat `/downloads/alsa-*': No such file or directory"[/quote] The ALSA guides are great, they always get my sound fixed, but they can be confusing to the unfamliar, I know.  Exactly which guide for which card are you using?  It does look like you have sound modules already loaded

[quote=nugglets]** snd                    48644  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_os  s,snd_pcm,snd_timer**[/quote]

The way to use the copy (cp) command is
```
cp /<source folder>/<source file> /<target folder>
``` The error you are getting is saying that the folder /downloads or the file /downloads/alsa-* doesn't exist.

Where did you download the ALSA source code (alsa-drivers, alsa-lib, etc) too?

Your desktop?  Another folder?

---

### Post by nugglets on 2006-05-30
Ok, so I figured out the copy command and got everything in the right spot.. but now when i go to "./configure --with-cards=atiixp --with-sequencer=yes;make;make install" i get an error about not finding a C compiler in $PATH

the guide i am trying to use is [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp#aso]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp#aso")

arg, at least im learning some stuff. thanks so far for all your help.

---

### Post by Sef on 2006-05-30
There have been problems with an AC 97.  Here's what I did to get it running.

Since you said you have done all the simple stuff (sound icon, alsamixer, and default sound checks), open a terminal and copy and paste the results from them in here.

cat /proc/asound/cards

gksudo /etc/modprobe.d/alsa-base

---

### Post by nugglets on 2006-05-30
> root@razorlives:/usr/src/alsa/alsa-driver-1.0.11# cat /proc/asound/cards
0 [IXP            ]: ATIIXP - ATI IXP
                     ATI IXP rev 2 with unknown codec at 0xc0503400, irq 17

the second one isnt outputting anything at all.

---

### Post by nugglets on 2006-05-31
Thanks for all your help guys. After poking around alot more, I noticed that Breezy hadnt detected alot more of my hardware than I realized. So I decided to look for another distro to check out. Then, on a whim, I decided to install the Dapper Release Candidate to see if, by chance, it would detect my hardware. At first it did not, so I was kindve dissapointed. Then realizing that I now had no internet, I had to reinstall XP. XP also did not properly install the vast majority of my hardware, but thankfully I have full driver CDs for all my windows PCs. 

So after getting a basic, clean windows install up and running a friend came over and asked me to show him Ubuntu(the cd was sitting on my desk). So, I pop in the Live CD and start poking around and notice my sound is working. After checking around, suddenly the Live CD had ALL of my hardware isntalled. This seemed really strange, so I setup some partitions and installed Dapper again. Everything worked flawlessly. 

Being the inquisitive person that I am, I was intrigued so I decided to test some things out. Did a clean format of the whole drive, and another base XP install only this time I didnt install any of the windows drivers. Restart, boot up the Dapper Live CD and again, no hardware is working properly. Install Dapper anyways, do all the updates, still no sound/video/WiFi working correctly. Go back into windows, install the drivers, restart and boot into Dapper again and still nothing. Reinstall Dapper, with the windows drivers all installed again, and right away everything was working properly. 

So, though I am very happy that I can use Ubuntu to the best abilities of my laptop now, I am still very confused as to how having the windows drivers installed is effecting my Ubuntu isntallation. I didnt have time to mess with it beyond that point, it was 2am by then and I had to work at 7am this morning, but I plan on going home and individually un-installing windows drivers and booting back into Dapper to see if it is effected. 

The only thing I could possibly think of to explain this was somehow the windows drivers and the shitty gateway bios are linked, but that seems like something I would have heard about before now. If that is, indeed, the case then I would be very, very disappointed. Anyone else run into this problem? Possibly even with other big-name(read: POS) vendors?

---

