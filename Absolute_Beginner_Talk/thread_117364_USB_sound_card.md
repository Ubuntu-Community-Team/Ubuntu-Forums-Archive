---
title: "USB sound card"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by george_apan on 2006-01-14
Hello all! I'm thinking of buying the Terratec Aureon 5.1 USB MKII sound card to add 5.1 sound to my laptop. Does anyone here have this card and can confirm that it works? Does it need any special tweeks or does it work out of the box?

Thanks for any hints.

George

---

### Post by 23meg on 2006-01-15
According to the pages below it seems to be compatible since it uses the snd-usb-audio module. 

[http://www.linuxquestions.org/hcl/showproduct.php/product/2866/sort/2/cat/all/page/1](http://www.linuxquestions.org/hcl/showproduct.php/product/2866/sort/2/cat/all/page/1)
[http://www.qbik.ch/usb/devices/showdev.php?id=3102](http://www.qbik.ch/usb/devices/showdev.php?id=3102)

---

### Post by george_apan on 2006-01-27
[QUOTE=23meg]According to the pages below it seems to be compatible since it uses the snd-usb-audio module. 

[http://www.linuxquestions.org/hcl/showproduct.php/product/2866/sort/2/cat/all/page/1](http://www.linuxquestions.org/hcl/showproduct.php/product/2866/sort/2/cat/all/page/1)
[http://www.qbik.ch/usb/devices/showdev.php?id=3102](http://www.qbik.ch/usb/devices/showdev.php?id=3102)[/QUOTE]
I just bought it today and can confirm that it works right out of the box perfectly. Using an alsa script I found in the following thread also makes xmms use all 5.1 speakers:
[http://ubuntuforums.org/showthread.php?p=302331](http://ubuntuforums.org/showthread.php?p=302331)
:)

---

### Post by luopio on 2006-09-18
(Running ubuntu edgy)

Just bought mine and I'm having trouble with just normal stereo sound: in the mixer I see *"Microphone",* *"Speaker"* and *"Speaker2"* in *"Playback"* (everything is enabled in preferences). *"Speaker"* is stereo, but doesn't come out of any of the outputs. *"Speaker2"* is mono and comes out of front and headphones.

When I set sound to use *"USB Audio"* in Preferences->Sound, Rhythmbox works nicely, but the sound is pretty crappy thanks to the mono output.

Any help would be greatly appreciated :cool: !

---

### Post by george_apan on 2006-09-18
Are you using ALSA for the sound output? If not go to System->Preferences->Multimedia chooser (or something like that, I'm not running an english ubuntu).

Now create a file in your home dir named .asoundrc with this inside:
> pcm.dmix51 {
	type dmix
	ipc_key 1024
	ipc_key_add_uid false
	ipc_perm 0666 
	slave {
		pcm "hw:1,0"
		channels 6
		period_time 0
		period_size 1024
		buffer_size 8192
		rate 48000
	}
}

ctl.dmix51 {
	type hw
	card 1
}

pcm.stereo {
	type plug
	slave.pcm "dmix51"
	ttable.0.0 1
	ttable.1.1 1
}

pcm.!default {
	type route
	slave.pcm "dmix51"
	slave.channels 6
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 1
	ttable.1.4 1
	ttable.0.5 1
	ttable.1.5 1
}

pcm.duplicate {
	type plug
	slave.pcm "dmix51"
	slave.channels 6
	route_policy duplicate
}


That should have you fixed for the stereo output at least.
If you want to play a video (like a DVD) with a 6ch ac3 sound with mplayer create a file ~/.mplayer/6ch.conf with the following content:
> # Use all 6 channels from an ac3 properly

ao=alsa:device=dmix51
channels=6
af=channels=6:6:0:0:1:1:2:4:4:2:3:5:0:3

Now whenever you want to play such a file use a command like 'mplayer -include ~/.mplayer/6ch.conf video.avi'. You can put this in an alias as I have:
alias mplayer6ch='mplayer -include ~/.mplayer/6ch.conf'
so you can just call it by 'mplayer6ch yourvideo.avi'

That's my exact setup and everything works great.

---

### Post by luopio on 2006-09-18
Thanks for the tip! I'm using ALSA and with that asoundrc I get sound from all the analog outputs. However the same problem persists: all the outputs are **mono**, or rather the one mono channel gets cloned to the other outputs.

Since I only have two speakers connected to the card, I would be more than happy with just stereo sound.. So you have a stereo channel in Alsa mixer? You can mute only the other speaker, etc.? 

I also reported this as a bug in ALSA here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2453](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2453)

---

### Post by george_apan on 2006-09-19
To be honest I never touched the alsa mixer before. Now that I did I get the same behaviour as you do, I can't independantly adjust levels on the two stereo channels.

But the sound is stereo anyway, I do not get the dual mono thing you are talking about. I have just created a wav with audacity that has alternating sound from left to right and plays perfectly with xmms...

---

