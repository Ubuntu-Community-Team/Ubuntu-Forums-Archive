---
title: "Creative Sound Blaster Extigy problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by kpfuser on 2007-08-14
After connecting an external (USB) sound card (Creative Sound Blaster Extigy), Feisty Fawn has been unable to play sound files (.wav). Running the command **aplay -l** shows that Extigy is recognized. Running **alsamixer** showed that some volume controls were muted. However, when this was corrected, the Totem Movie Player (which popped up as the default player when I doubleclicked my sample .wav file) appeared to be playing the sample file but without sound. It appears from the info in [http://ubuntuforums.org/showthread.php?t=205449&highlight=Extigy](http://ubuntuforums.org/showthread.php?t=205449&highlight=Extigy) that some drivers must be installed. However, no driver specific to my sound card seems to exist and the instructions about what to do next are not very clear to me because I am a Linux beginner. Could someone be able to come up with clear and concrete suggestions as to what to do next?

Thanks in advance!

---

### Post by linuxwizard on 2007-08-15
Also check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.


[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by kpfuser on 2007-08-16
Thanks for the reply. It didn't solve my problem but I am sure that it pointed the way to its eventual solution.

To begin with,
> Also check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF
is an instruction I have no idea how to carry out. The alsamixer GUI shows no such switches. Where can I find/reset them?

The first link was of great help. Through it I found that my system includes two sound cards. The default (index 0) is an on-board sound card. The Sound Blaster Extigy shows up as "1 snd_usb_audio." Unfortunately when I tried to make Extigy the default sound card by running **sudo nano /etc/modprobe.d/alsa-base options snd-usb-audio index=0 options snd-intel8x0 index=1** I was greeted with a many-a-line output and no clue about what to do next.

From the second link, I found that disabling the on-board sound card through the BIOS setup might solve the problem. Well, I tried it but it didn't. Now the "0 snd_intel8x0" sound card doesn't show up in the list of sound cards but Extigy continues to come up as "1 snd_usb_audio," i.e., it did not become the default sound card. At the same time, the alsamixer GUI doesn't load as it fails to locate the default sound card. Thus it would appear that there is no getting around to making Extigy the default sound card officially. Could anyone help me do this?

---

### Post by Arthur Archnix on 2007-08-16
Edit: Nevermind.

---

### Post by linuxwizard on 2007-08-16
To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab

Having 2 sound cards I have seen other posts about issues when using 2. Not sure what to tell you on that.

---

### Post by nilord on 2007-09-12
kpfuser! 

Does the front panel of your creative extigy work in ubuntu? (the volume knob, mic volume knob, cmss, etc.)

Because I also have Creative Extigy, but the knobs doesn't do anything. Please help! thanks!

---

### Post by kpfuser on 2007-09-13
> **nilord said:**
> kpfuser! 

Does the front panel of your creative extigy work in ubuntu? (the volume knob, mic volume knob, cmss, etc.)

Because I also have Creative Extigy, but the knobs doesn't do anything. Please help! thanks!
As in your case, the knobs do nothing at all. Ah well. next time we go shopping for a sound card we will be a little wiser. Running Extigy from a Win2k partition on the same pc I get much more functionality as well as the music player (the best one from the point of view of sound quality I have ever found) that comes with it. It is a pity that Creative does not manufacture truly Linux-compatible sound cards. I guess we should all tell them what we think about their business practices.

---

