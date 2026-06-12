---
title: "iMac 9,1 - 20inch - sound not working, intrepid"
date: 2009-03-15
forum: Apple Hardware Users
---

### Post by jamesey on 2009-03-15
I bought the newest generation of iMac yesterday, the iMac 9,1. I've immediately installed Ubuntu and everything works great except the sound. In the 10 minutes I messed around with MacOS while Ubuntu was downloading, sound did work. 

On my fresh install, I had a volume icon in the panel, but when I'd try an mp3 or video, no sound played. 

I searched around the forums and stupidly downgraded Intrepid's alsa driver to version 1.0.15. When I restarted, I got an error that no sound cards were available on the mac, and my volume icon in the panel has a red circle with a cross through it. 

How do I fix this? I'm sort of savvy, but not good with drivers. 

if I do aplay-l in terminal, I get "no soundcards found...." as output.

if I do lspci-v I get
```
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
	Memory at d3580000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```

---

### Post by jamesey on 2009-03-15
quick update, I installed Alsa drivers 1.19, my sound mixer works, I just don't hear anything. 

I can play an MP3 now, and see an equalizer doing it's thing, but I don't hear anything. the volume icon in my panel is no longer crossed out.

```
james@james-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by LiamWilson on 2009-03-15
have you tried running alsamixer?

---

### Post by jamesey on 2009-03-15
> **LiamWilson said:**
> have you tried running alsamixer?

this is all I get

---

### Post by jamesey on 2009-03-15
I accidentally posted this in another thread, but the info in pertinent to both. 

I went through the troubleshooting guide, here are my results

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

find /lib/modules/`uname -r` | grep snd
```
i wont paste them, but a load of *.ko files were found
```

lspci -v
```
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at d3580000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I went here [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

I think that is my video card
In terminal i typed
modinfo soundcore
and got

```
filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 

```

in terminal i did
gksudo gedit /etc/modprobe.d/options
and added "options snd_hda_intel model=mac24" 
I restarted and still no sound

---

### Post by jamesey on 2009-03-15
I've read a few posts across various forums that suggest adding a line to the /etc/modprobe.d/option file. There seem to be a handful of differences over the proper syntax

which of these is right?
"options snd-hda-intel model=imac24"
"options snd_hda_intel model=imac24"
"options snd-hda-intel model=mac24"
"options snd_hda_intel model=mac24"

also I read [here]("https://help.ubuntu.com/community/Intel_iMac"), 
> If you have an Aluminium Imac setting in /etc/modprobe.d/alsa-base the option model=mbp3 make sound work without patching anything. I'm not quite sure if that applies to me, and if the mbp3 variable is right.

---

### Post by jamesey on 2009-03-15
I feel like I'm spamming my own thread, but I'm hoping someone will see something that will solve this sound issue on the new iMac

I'm playing an mp3, and the pulse audio applet volume meter is showing an equalizer pumping away. Totem is showing an equalizer moving to the music too

there's just nothing coming out of the speakers.

edit: I just tried the headphone jack and there was sound coming out. It scared the **** out of me because I wasnt expecting that. 

how the heck do I make my speakers the default audio output instead of my headphone jack?

---

### Post by buttertoad on 2009-03-15
This seems to be the same thing going on with the MacBook Pro(5,1).

Unfortunately I'm in the same boat as you (headphones work but speakers don't) so I can't offer a solution. I know people smarter then me are working on this problem and I imagine that it will solve both our issues.

Here is the link the ongoing MacBook Pro sound issues: [http://ubuntuforums.org/showthread.php?t=971236]("http://ubuntuforums.org/showthread.php?t=971236")

---

### Post by jamesey on 2009-03-16
it's gotta be something obvious. Sound clearly works. It's just not coming out of the correct output.

---

### Post by cyberdork33 on 2009-03-16
try: 
```
alsamixer -c 0
```

as shown in the FAQ. That should allow you to adjust the mixer levels for you card instead of pulseaudio.

---

### Post by jamesey on 2009-03-16
> **cyberdork33 said:**
> try: 
```
alsamixer -c 0
```

as shown in the FAQ. That should allow you to adjust the mixer levels for you card instead of pulseaudio.


something doesnt look quite right with this. I just don't know what it is. 
Also, I thought I upgraded my alsa to 1.0.19 but this screenshot says 1.0.17

---

### Post by cyberdork33 on 2009-03-16
yea that does look weird, but if you are not passing the right module option it will not look right either... (but I don't think any of those module options are right for you. This is new sound hardware from the other iMacs, and it may just not work yet... sorry.)

You can have a look in the gnome sound mixer to see if you can use the OSS channels... otherwise, you probably need to file a bug with ALSA. Have you seen this hardware in any other computer out there?

---

### Post by jamesey on 2009-03-16
> **cyberdork33 said:**
> yea that does look weird, but if you are not passing the right module option it will not look right either... (but I don't think any of those module options are right for you. This is new sound hardware from the other iMacs, and it may just not work yet... sorry.)

You can have a look in the gnome sound mixer to see if you can use the OSS channels... otherwise, you probably need to file a bug with ALSA. Have you seen this hardware in any other computer out there?

I've looked all around, I haven't seen any Ubuntu users with the new iMac that came out on March 3. I have other OSS channels, nothing plays.

---

### Post by jamesey on 2009-03-18
I ran a live cd with Jaunty 9.04, still no sound by defualt

aplay -l
```
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

if Alsamixer sees that, it means the iMac 9,1 soundcard is supported to some degree right? 
browsing through some change logs, ALC 883 has been supported since alsamixer 1.0.11.

---

### Post by cyberdork33 on 2009-03-18
> **jamesey said:**
> browsing through some change logs, ALC 883 has been supported since alsamixer 1.0.11.
not necessarily apple's version of it though... they do weird stuff sometimes.

did you try the alsamixer command in the livecd environment?

---

### Post by jamesey on 2009-03-18
> **cyberdork33 said:**
> not necessarily apple's version of it though... they do weird stuff sometimes.

did you try the alsamixer command in the livecd environment?

yeah same result. :(

I upgraded my nvidia drivers from 177 to 180. that wasn't any help.

---

### Post by cyberdork33 on 2009-03-19
I'd file a bug... I think you just have a case of unsupported hardware.

---

### Post by PhoenixP3K on 2009-03-30
Working solution (in my case)

[Bug report follow up]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323116")

> Adding 

options snd-hda-intel model=auto

to /etc/modprobe.d/alsa-base and rebooting solved the problem.

So:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Then add "options snd-hda-intel model=auto" at the end, and save the file and reboot.

This seems to work only if you have ALC883 as your sound card.

---

### Post by jamesey on 2009-03-30
> **PhoenixP3K said:**
> 

This seems to work only if you have ALC883 as your sound card.

When I do aplay -l in terminal, I am told my playback device is ALC 883. 

If I install gnome sound mixer, I am told my playback device is ALC889A. 

Unfortunately adding the model as "auto" didn't work for me :(

---

### Post by hirnsaege on 2009-03-30
I had the same issue with the card getting recognised but not being able to play any sound as a normal user (and from X environment), whereas *sudo aplay xy.wav* worked fine. Doing *chmod 666 /dev/snd/** solved it for me on Intrepid-ppc.

---

### Post by jamesey on 2009-04-03
> **cyberdork33 said:**
> I'd file a bug... I think you just have a case of unsupported hardware.

I filed a bug at launchpad and someone was awesome enough to make a patch that gets the speakers working. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

just one small problem...I don't know how to apply the patch. Can anyone point me to a quick guide for doing so?

I'm currently working on Jaunty Beta with alsa 1.0.18

---

### Post by cyberdork33 on 2009-04-03
> **jamesey said:**
> I filed a bug at launchpad and someone was awesome enough to make a patch that gets the speakers working. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

just one small problem...I don't know how to apply the patch. Can anyone point me to a quick guide for doing so?

I'm currently working on Jaunty Beta with alsa 1.0.18
well... this is not easy... might have to wait till it is fixed, but you will have to get the source for alsa 1.0.18, then apply the patch... with the patch command... [http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)
Then you have to compile and install it.

If Micah said he would make debs, I would just wait for that.

---

### Post by jamesey on 2009-04-03
> **cyberdork33 said:**
> well... this is not easy... might have to wait till it is fixed, but you will have to get the source for alsa 1.0.18, then apply the patch... with the patch command... [http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)
Then you have to compile and install it.

If Micah said he would make debs, I would just wait for that.

I was afraid of that. i'll just wait. thanks.

---

### Post by DShad on 2009-04-13
> **jamesey said:**
> I was afraid of that. i'll just wait. thanks.

Any news about the debs?

I'm stuck witt NO SOUND at all using Ubuntu Jaunty beta with my new iMac 9,1.

Can't wait to get my sound back...

---

### Post by cyberdork33 on 2009-04-13
> **DShad said:**
> Any news about the debs?

I'm stuck witt NO SOUND at all using Ubuntu Jaunty beta with my new iMac 9,1.

Can't wait to get my sound back...
Please follow the bug report:
[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

Micah never posted the debs, but maybe if you posted a reminder....

Also, the bug is currently marked incomplete because nobody has provided information about whether the input jack works. Please someone give feedback!

---

### Post by jamesey on 2009-04-13
> **DShad said:**
> Any news about the debs?

I'm stuck witt NO SOUND at all using Ubuntu Jaunty beta with my new iMac 9,1.

Can't wait to get my sound back...

You should be able to get the headphone jack working fairly easily for sound output. It sucks, but that's a temporary solution for now. As for the speakers, there is a patch that will work for ALSA 1.0.18 but I don't know how to apply it.

---

### Post by DShad on 2009-04-13
> **jamesey said:**
> You should be able to get the headphone jack working fairly easily for sound output. It sucks, but that's a temporary solution for now. As for the speakers, there is a patch that will work for ALSA 1.0.18 but I don't know how to apply it.

In my case, I have NO SOUND whatsoever.

No sound from internal speakers and nothing comes out if I plug external speakers into headphone jacks.

In other words, I cannot enjoy my freshly installed Ubuntu Jaunty beta because of that.

If you need any more information, jst let me know.  I'm willing to provide any info at all to solve this issue.

Marc

---

### Post by cyberdork33 on 2009-04-13
> **DShad said:**
> In my case, I have NO SOUND whatsoever.
Did you add the ALSA module options as shown earlier in this thread?

---

### Post by DShad on 2009-04-13
> **cyberdork33 said:**
> Did you add the ALSA module options as shown earlier in this thread?

I tried different options (like "options snd-hda-intel model=auto or "options snd-hda-intel model=imac24") but same result.

The only thing I haven't tried is to apply the patch and  compile the latest alsa modules...  because I'm not sure enough how to do it.

Marc

---

### Post by cyberdork33 on 2009-04-13
> **DShad said:**
> I tried different options (like "options snd-hda-intel model=auto or "options snd-hda-intel model=imac24") but same result.

The only thing I haven't tried is to apply the patch and  compile the latest alsa modules...  because I'm not sure enough how to do it.

Marc
did you try 'mbp3'?

---

### Post by jamesey on 2009-04-13
> **DShad said:**
> I tried different options (like "options snd-hda-intel model=auto or "options snd-hda-intel model=imac24") but same result.

The only thing I haven't tried is to apply the patch and  compile the latest alsa modules...  because I'm not sure enough how to do it.

Marc

on my iMac 20" (9,1), the option imac24 gets the head phone jack working. 
what's your output for 
aplay -l  ??

---

### Post by DShad on 2009-04-14
> **jamesey said:**
> on my iMac 20" (9,1), the option imac24 gets the head phone jack working. 
what's your output for 
aplay -l  ??

Here's what I get from aplay -l:

**** Liste des PLAYBACK périphériques ****
carte  0: NVidia [HDA NVidia], périphérique 0 : ALC883 Analog [ALC883 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 1 : ALC883 Digital [ALC883 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
marc@marc-ubuntu:~$ 


What's next?

Marc

---

### Post by DShad on 2009-04-14
I'm not quite sure here... Is it "sudo gedit /etc/modprobe.d/alsa-base" or "sudo gedit /etc/modprobe.d/alsa-base.conf" I need to do?

Thanks

---

### Post by jamesey on 2009-04-14
Here is what I have to get at least the headphones working

this is all that is in my alsa-base file. 

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=imac24
```


and here is my alsa-base.conf file.
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

I would try modifying the alsa-base first, restarting, and seeing if your headphone jack works. If not, find what's different between my alsa-base.conf file and yours.

---

### Post by DShad on 2009-04-14
Thank you jamesey,

I thought I had to add that line at the alsa-base.conf.  I had NO alsa-base file...  So I created one and put imac24.

Now my headphone jack works, but not the internal speakers.  Think I'm at the same point you are right now but at least I have sound!

Thanks

Marc

---

### Post by jamesey on 2009-04-14
glad to hear the headphone jack works now. that's better than nothing. I have some shitty dell speakers hooked up to mine.

You can get the iMac speakers to work if you know how to apply a driver patch. Otherwise you'll have to wait patiently like me. see here 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

---

### Post by slurms on 2009-04-29
I followed what was written this thread with a few minor additions to get my 20" imac working with headphones and speakers. Here is my alsa-base.conf file:

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=mbp3

```

I only modified the bottom two lines. Apparently you need to have things in /etc/modprobe.d/alsa-base.conf now rather than /etc/modprobe.d/alsa-base (it needs to be .conf in the future).

After the addition of these two lines, restarting alsa and pulseaudio, my sound now works out of both speaker and headphones :)

---

### Post by jamesey on 2009-04-29
thanks slurms, but that only works in iMac 8,1. 

iMac 9,1 has slightly different hardware

---

### Post by jamesey on 2009-09-02
seems the official fix is still elusive. hopefully 9.10 fixes everything.

---

### Post by moporoco on 2009-12-14
Running 9.10 final release with latest patches and still not working. Any news?

---

### Post by jamesey on 2009-12-14
> **moporoco said:**
> Running 9.10 final release with latest patches and still not working. Any news?

apparently it works in pulseaudio 1.21 but karmic ships with pulseaudio 1.20. Guess we'll have to wait until april.

---

### Post by linuxopjemac on 2009-12-14
Why don't you compile it yourself. The tar file can be downloaded from the website:
[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by texadactyl on 2009-12-29
This worked for me on several iMacs, Intrepid to Lynx:
1. !cd /etc/modprobe.d
2. !sudo gedit alsa-base.conf
3. At the end, add this line:
options snd-hda-intel model=mac24
4. Comment out (#) any other "options snd-hda-intel" lines.

Make sure that your audio is set to Analog Stereo Output if you are using the built-in iMac speakers.

Oh well, the list of the work-around post-install actions has shrunk considerably.

---

### Post by 311005901 on 2010-01-14
> **lemon8h8ead said:**
> This worked for me on several iMacs, Intrepid to Lynx:
1. !cd /etc/modprobe.d
2. !sudo gedit alsa-base.conf
3. At the end, add this line:
options snd-hda-intel model=mac24
4. Comment out (#) any other "options snd-hda-intel" lines.

Make sure that your audio is set to Analog Stereo Output if you are using the built-in iMac speakers.

Oh well, the list of the work-around post-install actions has shrunk considerably.

Well, this does NOT work for me. :|
I had my fingers crossed...

Intel iMac 9,1 24in
Ubuntu Karmic

---

### Post by linuxopjemac on 2010-01-15
did you try the backport alsa module and unmute all channels with alsamixer?

```
aptitude install linux-backports-modules-alsa-karmic-generic
```

---

### Post by knattlhuber on 2010-03-10
> **linuxopjemac said:**
> did you try the backport alsa module and unmute all channels with alsamixer?

```
aptitude install linux-backports-modules-alsa-karmic-generic
```

Thanks! The backport module fixed it for me.

---

### Post by jamesey on 2010-03-15
I did this on Lucid (10.04 alpha 3) 
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32&p=103#p103](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32&p=103#p103)
and now I have sound on my iMac's speakers with Ubuntu.

The sound is a bit tinny, but it will do for now.

---

### Post by MikaelHolber on 2010-04-20
I've been following this thread for a year now. I found this on my hunt for Lucid upgrade info.

[I][http://mac.linux.be/content/more-apple-improvements-kernel-2633](http://mac.linux.be/content/more-apple-improvements-kernel-2633)
[/I]
Seems like the 2.6.33 will contain an update for these Imacs. The "tiny" sound comes from that the internal subwoofer is deactivated. If anyone running Lucid can upgrade to the PPA kernel and try around a bit this would be great! 

I use my Imac as my primary machine and dare not to upgrade before the official release.

---

### Post by MikaelHolber on 2010-04-21
Okay!

I tried installing Lucid on another partition and with great success! After installing the 2.6.33-kernel from launchpad ppa-kernel and setting **/etc/modprobe.d/alsa-base.conf** to **options snd-hda-intel model=imac91** i got sound from the speakers. Comparing the sound with **mbp3** and **lenovo-sky** I think this is closer to the real potential of these speakers. Good base response and clear sound. 

Unfortunately, the nvidia-driver didn't work with this kernel so I have moved back to 2.6.32 and await further releases.

---

### Post by jamesey on 2010-04-21
> **MikaelHolber said:**
> Okay!

I tried installing Lucid on another partition and with great success! After installing the 2.6.33-kernel from launchpad ppa-kernel and setting **/etc/modprobe.d/alsa-base.conf** to **options snd-hda-intel model=imac91** i got sound from the speakers. Comparing the sound with **mbp3** and **lenovo-sky** I think this is closer to the real potential of these speakers. Good bass response and clear sound. 

Unfortunately, the nvidia-driver didn't work with this kernel so I have moved back to 2.6.32 and await further releases.

That's excellent. Will 2.6.33 be in the final Lucid release?

---

### Post by linuxopjemac on 2010-04-22
Excellent news for the imac9,1 boys and girls. The new kernel does fix the audio problem apparently, as it was promised. Just wait for a stable enough Lucid and upgrade.

---

### Post by MikaelHolber on 2010-04-22
> **jamesey said:**
> That's excellent. Will 2.6.33 be in the final Lucid release?

It seems like the 2.6.32 will be in the final release. Hopefully the alsa fix will be available in the back ported modules. Have yet to try this when I get back home. 

What is different (if it works) is that the channel selection will appear in the alsamixer if everything is correct. This is not available with the model=imac24. Set this to 4 channels and it should work (if I remember correctly)

---

### Post by MikaelHolber on 2010-04-24
**Success!**
I installed the **linux-backports-modules-alsa-lucid-generic** and used the options **model=imac91** and now I got sound from speakers and bulk lucid otherwise. 

Don´t forget to select 4ch.

---

### Post by jamesey on 2010-04-24
> **MikaelHolber said:**
> **Success!**
I installed the **linux-backports-modules-alsa-lucid-generic** and used the options **model=imac91** and now I got sound from speakers and bulk lucid otherwise. 

Don´t forget to select 4ch.

in 2.6.32 or 2.6.33?

---

### Post by MikaelHolber on 2010-04-24
> **jamesey said:**
> in 2.6.32 or 2.6.33?

2.6.32, the release version for Lucid.

---

### Post by linuxopjemac on 2010-04-26
SUPER, I will publish this on my own site.

---

### Post by jamesey on 2010-09-04
I did a fresh install of MM 10.10 beta. To get sound working, you just have to go to  **/etc/modprobe.d/alsa-base.conf** and add the line **snd-hda-intel model=imac91**.

Then **in terminal enter "alsamixer"**, and max out the volume on each bar. Then in sound preferences, go to the hardware tab and **choose the "analog stero output option.**" 

Sound will work perfectly and the tinny quality is gone. The speakers finally sound how they should.

---

### Post by linuxopjemac on 2010-09-04
good news jamesey

---

### Post by houndi on 2010-09-05
'm playing an mp3, and the pulse audio applet volume meter is showing an equalizer pumping away. Totem is showing an equalizer moving to the music too

---

