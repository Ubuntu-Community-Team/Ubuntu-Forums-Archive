---
title: "Persistantly Poor Sound Quality in Ubuntu with C2D Macbook."
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by guywithcable on 2008-08-19
I have a Core 2 Duo Macbook

```
hunter@hunter-laptop:~$ sudo dmidecode | grep Mac
    Product Name: MacBook3,1
    Family: MacBook
    Product Name: Mac-F22788C8
    Version: Mac-F22788C8
```with the following audio card:

```
hunter@hunter-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```My problem is that the audio is very poor quality. It is especially noticeable at high volumes (over 50%). It sounds very tinny, like a really cheap hand-held radio. The audio sounds fine in OS X, so it is a Linux problem. After a lot of research I have found two possible explanations. I do not know if either of these is actually causing the problem, just that someone has stated they could be.

     1. There is a hardware equalizer that ALSA cannot take advantage of, which is causing the distortion.
     2. There is a third speaker for low frequency sound which is not being utilized.

Running speaker-test:

```
hunter@hunter-laptop:~$ speaker-test -c8 -twav -l 1

speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 8 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
Time per period = 11.050963
```I only hear front left and front right, so I assume it is not explanation #2. I have tried several solutions, which have all failed, including (but not limited to):

- Implementing a system wide PulseAudio equalizer (following a howto on the forums.)
- Adding various lines to /etc/modprobe.d/alsa-base and /etc/modprobe.d/options including:
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && { /lib/alsa/modprobe-post-install snd-hda-intel ; }
options snd_hda_intel model=mbp3
options snd_hda_intel model=intel-mac-v1 (through v5)
options snd_hda_intel model=macbook
- Adjusting the surround setting in alsa-mixer (which only shows up when the sound isn't working.)

The only of the lines above to work were the first two. And the first one only works when the second is present, so I assume it doesn't matter.

Please help me, this terrible audio is driving me crazy.

---

### Post by pokipoki08 on 2008-08-20
You may want to try this

login to failsafe terminal only at the login window screen
unload all modules related to sound (use lsmod* to find out, there's many sound modules)
sudo modprobe snd_hda_intel
logout
login as per normal

```

lsmod > lsmod.txt
```

in this text file you can see many modules
remove all other modules unrelated to sound
create a script to unload sound modules like this

```
#!/bin/sh
sudo rmmod snd_pcsp ;
sudo rmmod snd_hda_intel ;
sudo rmmod snd_pcm_oss ;
sudo rmmod snd_mixer_oss ;
sudo rmmod snd_pcm_oss ;
sudo rmmod snd_pcm ;
sudo rmmod snd_hda_intel ;
sudo rmmod snd_pcm_oss ;
sudo rmmod snd_page_alloc ;
sudo rmmod snd_hda_intel ;
sudo rmmod snd_pcm ;
sudo rmmod snd_hwdep ;
sudo rmmod snd_pcsp ;
sudo rmmod snd_hda_intel ;
sudo rmmod snd_seq_dummy ;
sudo rmmod snd_seq_oss ;
sudo rmmod snd_seq_midi ;
sudo rmmod snd_rawmidi ;
sudo rmmod snd_seq_midi ;
sudo rmmod snd_seq_midi_event ;
sudo rmmod snd_seq_oss ;
sudo rmmod snd_seq_midi ;
sudo rmmod snd_pcsp ;
sudo rmmod snd_seq ;
sudo rmmod snd_seq_dummy ;
sudo rmmod snd_seq_oss ;
sudo rmmod snd_seq_midi ;
sudo rmmod snd_seq_midi_event ;
sudo rmmod snd_timer ;
sudo rmmod snd_pcm ;
sudo rmmod snd_pcsp ;
sudo rmmod snd_seq ;
sudo rmmod snd_seq_device ;
sudo rmmod snd_seq_dummy ;
sudo rmmod snd_seq_oss ;
sudo rmmod snd_seq_midi ;
sudo rmmod snd_rawmidi ;
sudo rmmod snd_seq ;
sudo rmmod snd_pcsp ;
sudo rmmod snd ;
sudo rmmod snd_hda_intel ;
sudo rmmod snd_pcm_oss ;
sudo rmmod snd_mixer_oss ;
sudo rmmod snd_pcm ;
sudo rmmod snd_hwdep ;
sudo rmmod snd_seq_dummy ;
sudo rmmod snd_seq_oss ;
sudo rmmod snd_rawmidi ;
sudo rmmod snd_seq ;
sudo rmmod snd_pcsp ;
sudo rmmod snd_timer ;
sudo rmmod snd_seq_device ;
sudo rmmod soundcore ;
sudo rmmod snd ;
sudo rmmod snd_pcsp ;
```

---

### Post by guywithcable on 2008-08-20
No luck. It says they're in use. How do I kill anything that is using them?

---

### Post by volanin on 2008-08-20
Try this:

```
$ alsamixer -c0
```

You should see a few audio channels.
And unmute (pressing M) all the channels and put them at maximum volume.
:)

---

### Post by guywithcable on 2008-08-20
> **volanin said:**
> Try this:

```
$ alsamixer -c0
```You should see a few audio channels.
And unmute (pressing M) all the channels and put them at maximum volume.
:)

I tried. All channels are unmuted and the audio is still terrible. I've read elsewhere that some people have a surround channel that fixes this issue, but I only have a surround channel when I set the model in alsa-base to something that doesn't work. :(

Do you have the same card as me? (82801H)

---

### Post by volanin on 2008-08-21
> **guywithcable said:**
> I tried. All channels are unmuted and the audio is still terrible. I've read elsewhere that some people have a surround channel that fixes this issue, but I only have a surround channel when I set the model in alsa-base to something that doesn't work. :(

Do you have the same card as me? (82801H)

```
$ sudo dmidecode | grep Mac

Product Name: MacBook2,1
Family: MacBook
Product Name: Mac-F4208CAA
Version: Mac-F4208CAA

$ lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) HD Audio Controller (rev 02)
```
:(

---

### Post by guywithcable on 2008-08-21
> **volanin said:**
> ```
$ sudo dmidecode | grep Mac

Product Name: MacBook2,1
Family: MacBook
Product Name: Mac-F4208CAA
Version: Mac-F4208CAA

$ lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) HD Audio Controller (rev 02)
```:(

Is there a big difference between the ICH7 and the ICH8 family? Could that be the root of the problem?

---

### Post by guywithcable on 2008-08-23
Can anyone help me with this problem?

---

### Post by guywithcable on 2008-08-25
After completely removing ALSA with Synaptic, the problem still remains. I'm confused as to how sound still works with ALSA and it's conf files removed...

---

### Post by FiggyG on 2008-08-25
Hi there. I don't have a Mac, but I can give this a shot. I just fixed a sound problems tonight with my CA0106 (Audigy SE) and am feeling very adventurous. From you first post, it doesn't look like you've tried to use an updated version of alsa yet. So, let's begin there.

1. [Download]("http://www.alsa-project.org/main/index.php/Main_Page") the alsa-driver, alsa-lib, and alsa-util into a directory like ~/alsa. I'm using 1.0.17.

2. We need to have everything to compile said driver and files.
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

3. Let's copy and extract the files to where we need them for compiling.
```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```
4. Time to get dirty and compile everything!
```
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```
5. Reboot.

---

### Post by guywithcable on 2008-08-25
Should I remove ALSA and ALSA-Utils with Synaptic first?

---

### Post by 3strandchords on 2008-08-25
Same problem on my 3.1 MacBook... Only getting sound from 'front-left' and 'front-right' speakers.  Published fixes suggest unmuting surround sound either via the volume control properties or by installing the ALSA mixer.

In my case, neither seems to have a channel for surround sound...

Thanks.

---

### Post by FiggyG on 2008-08-25
You probably can remove it. I didn't remove alsa from synaptic though and it still works fine.

---

### Post by guywithcable on 2008-08-26
> **FiggyG said:**
> You probably can remove it. I didn't remove alsa from synaptic though and it still works fine.

Well, I tried it, and unfortunately, it didn't work. Do you think this is a problem with ALSA or PulseAudio? Can you explain to me the difference between the two?

---

### Post by cyberdork33 on 2008-08-26
> **guywithcable said:**
> Well, I tried it, and unfortunately, it didn't work. Do you think this is a problem with ALSA or PulseAudio? Can you explain to me the difference between the two?
ALSA is the actual driver. It interfaces with the hardware. 
PulseAudio is a soundserver.
[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by guywithcable on 2008-09-08
Does anyone know whether this is a bug in ALSA or something else? If you need any more info about my system, I'd be happy to provide it.

---

### Post by guywithcable on 2008-09-11
Now my audio doesn't work at all. I don't know what caused it, but I can't get sound, even by doing all the things I mentioned in my original post. :(

Please help me.

---

### Post by cyberdork33 on 2008-09-11
There is a bug report here.
[https://bugs.edge.launchpad.net/mactel-support/+bug/162347](https://bugs.edge.launchpad.net/mactel-support/+bug/162347)

---

### Post by guywithcable on 2008-09-15
I got audio working again after reinstalling anything alsa in Synaptic. That bug report doesn't give me any new information unfortunately, but thanks for pointing it out. Does anyone have any other suggestions? Is this bug going to be fixed in Intrepid? Would it be safe to try installing the alpha of Intrepid (i.e. has anyone with a Macbook tried already)?

---

### Post by cyberdork33 on 2008-09-15
not on a macbook, but I have been running it on my iMac and it is pretty stable.

If nothing else you can just tryout the LiveCD.

---

### Post by Tafari on 2008-10-06
I have the same problem on a C2D 4.1 macbook, I can't seem to find a fix for it either, but the sound quality is absolutely horrid. No one has figured anything out for this yet?

---

### Post by theevilhamster on 2008-10-15
:)thanks, alsamixer mixed my sound, its been bugging me for ages and i was told i needed a new sound driver that was very hard to install. im sorry you were not able to fix your sound, but i wish you the best of luck in doing so.

---

### Post by Kooothor on 2008-10-22
I up this topic.
I encounter the same problem with another distrib, on iMac Alu.

Is alsa so shitty that it can manage only two of the 8 channels ?

---

### Post by regebro on 2008-11-18
For those where this *does* work, could you show the output of
  lspci -v | grep Audio
and 
   sudo more /proc/asound/Intel/codec#0  | grep Codec

I'd like to try to figure out what the difference is. 
For me it is:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

Codec: Realtek ALC889A

---

### Post by regebro on 2008-11-18
OK, I'm getting somewhere now. 

When people say they fix the problem by enabling the Surround channel, they have the wrong board model loaded, because I read the source code for the realtek codec thingy, and it clearly thinks that all macbooks should use the same driver, and will autodetect MacBooks based on the subsytem ID, and it's the same one as lspci says. So, the detection seems to work correctly, and the correct model is "mbp3".

However, that model does *not* have a Surround channel.

So, assuming that it is correct that all MacBooks have a third speaker, the problem is simply that the Realtek Codec doesn't know about it. So a bug report needs to filed. :-/

---

### Post by guywithcable on 2008-11-19
> **regebro said:**
> OK, I'm getting somewhere now. 

When people say they fix the problem by enabling the Surround channel, they have the wrong board model loaded, because I read the source code for the realtek codec thingy, and it clearly thinks that all macbooks should use the same driver, and will autodetect MacBooks based on the subsytem ID, and it's the same one as lspci says. So, the detection seems to work correctly, and the correct model is "mbp3".

However, that model does *not* have a Surround channel.

So, assuming that it is correct that all MacBooks have a third speaker, the problem is simply that the Realtek Codec doesn't know about it. So a bug report needs to filed. :-/

Thanks for the information. :) Are you going to file it?

---

### Post by regebro on 2008-11-19
I found an existing bug which I updated with some info:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4086](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4086)

---

### Post by jdong on 2008-11-19
I believe on some of these models, there's a Surround channel which actually acts as some sort of low-pass or high-pass filter (i.e. it either attenuates/distorts bass or treble). Play around with all the mixer sliders to see if you can get audio quality better.

---

### Post by regebro on 2008-11-19
The point is that there is no surround channel when you use the (correct) mbp3 model. If you have one, it would be very helpful to know your configuration.

---

### Post by vidmode on 2009-03-17
Since people generally don't read bug reports (myself included), I'll paste what I pasted at the bottom of the alsa-project page:

On my Macbook 4,1, running a stock Ubuntu 8.10, kernel 2.6.27-11-generic, alsa version 1.0.17
The magic options bit that makes bass work on mine is a kernel option when inserting the snd_hda_intel module:

model=asus-a7m

The PCM level seems to control some(all, maybe) of the bass woofer. I'm not sure if all of the woofer is entirely all there though. Might be, would need to get two macbooks next to each other with the same piece of music to see. My hunch is that it isn't. Its more bassy than than the auto detected config, however.

I'll add this also to the ubuntu-bugs page, in the hope that someone, somewhere sees it :)

To change/test the module on the fly, you're going to have to killall pulseaudio, pommed, and mixer_applet2

Don't mash the Don't Reload button, or the Reload button on the dialog that pops up until you've finished messing with the modules, but before you reboot - the applet when running holds open a interface to the module (file descriptor) and will stop it unloading. (even with rmmod -f)

Here's the step by step instructions that you can try:

In a terminal:

```
sudo killall pulseaudio pommed mixer_applet2
totem /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel model=asus-a7m
totem /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

```

Prior to playing the file again, you may need to start gnome-alsamixer, and push up the Master, PCM, and Front volume sliders.
```

sudo apt-get install gnome-alsamixer

```

To make this permanent, edit the file ***/etc/modprobe.d/options***
Add the line:
```

options snd-hda-intel model=asus-a7m

```
Somewhere in the file, (I've put it at the top). Reboot. Theoretically, it should start with some bass. 

Cheers,
David

---

