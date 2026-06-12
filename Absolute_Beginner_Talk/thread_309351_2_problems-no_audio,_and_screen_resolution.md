---
title: "2 problems-no audio, and screen resolution"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by strabo on 2006-11-29
Hey all. I just installed Ubuntu, and have been trying to figure out how to do two things:

First, I want to change my resolution from the 1024 to 1280, but it won't let me. I have already looked around to try to see how to do this, but I still don't understand how.

Secondly, how do I go about getting my speakers to work? I use an SB Audigy from Creative, and it doesn't work. I assume that I need a driver, but I can't find anything in the Synaptic. Is there a fix, or will I have to stick to the integrated audio?

Thanks in advance for any help.

---

### Post by sindrum_murdnis on 2006-11-29
Just wondering if you found the settings under the system menu? Im not at on ubuntu right now but on the top bar click system, system tools maybe ... something up there, And just look for screen resolution option. Should be able to fix it there. hope this helps

---

### Post by christhemonkey on 2006-11-29
1. Go to a command line and edit this file /etc/X11/xorg.conf (heres how:)

```
gksudo gedit /etc/X11/xorg.conf 
```
And then look for the subsection about "Display" and make sure this line is there (in some shape or form!):
```
"Display"
Modes     "1024x768"
```

As for your sound card, what sort of Audigy is it?

If it is an SB Audigy X-Fi or an Sound Blaster Audigy 2 ZS Video Editor USB, then im afraid your out of luck and that onboard is what your gonna need to use.
If it is any other of the Audigy series it **should** "just work".


Could you post the output of this command?
```
lsmod | grep emu 
```

---

### Post by strabo on 2006-11-29
Where is the command line?


My soundcard is PCI, and the Ubuntu device manager tells me that it's just an SB Audigy. Should I bother opening my tower to take a look at it?

Also-How do I set VLC as the default media player for Ubuntu?

---

### Post by christhemonkey on 2006-11-29
For the terminal:
```
Applications > Accessories > Terminal
```

Could you post the output of that command i gave you previously?

And the output of:
```
lspci | grep Audigy
```

---

### Post by strabo on 2006-11-29
Yes, it does show the options for display, but it doesn't show 1280x1024. It only shows 1024x768 and lower.

Here is that display section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Also, here is what it spat at me after I typed in that other thing:

snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  1 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  2 snd_emu10k1,snd_intel8x0
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_pcm                84612  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd                    58372  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_intel8x0,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_timer
snd_page_alloc         11400  3 snd_emu10k1,snd_intel8x0,snd_pcm


Hope you can make some sense of that, because I have no idea.

---

### Post by christhemonkey on 2006-11-29
Ok, obviously i meant to change it like this (changes in bold!):
> Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes **"1280x1024" **"1024x768" "800x600" "640x480"
EndSubSection
EndSection


That output from the command i asked you to type shows that your sound card driver is indeed loaded and detected.
What is the output of this command?
```
aplay -l 
```

and if you have a handy .wav file lying around...:
```
aplay /path/to/wav/file.wav 
```

---

### Post by strabo on 2006-11-30
Here is the information that it gave me after the command:

strabo@strabo-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Even when I install VLC and try to play one of my movies, it still doesn't work.
Thanks for your help so far.

EDIT: When I go to System/Preferences/Screen Resolution, it still only gives me the 1024x768 thru 640x480 options. What should I do?

---

### Post by christhemonkey on 2006-11-30
You have to restart your pc for the screen resolution to take effect (technically only your X server needs to restart, but you might as well do a full restart)

Im sure you have, but im just checking, you have gone into the mixer and selected to use the right card and made sure everything is un-muted and turned up?

---

