---
title: "Can't get sound to play."
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Computer Junkie on 2008-03-21
Today I downloaded Ubuntu onto an old computer that I recently acquired after trying many different distros, but for some reason i can't get the sound to work at all. I have gone through every step I was supposed to do in the sound troubleshooting guide and simply can't figure out what to do. Ubuntu is really amazing and it would be a shame if I couldn't get the sound to work. I'm wondering if anybody could spend a little time helping me fix this problem. I've tried so many things that I think it might be a small problem I missed. Here is what I got when I typed asplay -1: 

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I also got 00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
when I did lspci. I'm really new to linux, so I'm having issues figuring out exactly what is wrong. Any help is greatly appreciated.:)

---

### Post by billgoldberg on 2008-03-21
> **Computer Junkie said:**
> Today I downloaded Ubuntu onto an old computer that I recently acquired after trying many different distros, but for some reason i can't get the sound to work at all. I have gone through every step I was supposed to do in the sound troubleshooting guide and simply can't figure out what to do. Ubuntu is really amazing and it would be a shame if I couldn't get the sound to work. I'm wondering if anybody could spend a little time helping me fix this problem. I've tried so many things that I think it might be a small problem I missed. Here is what I got when I typed asplay -1: 

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I also got 00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
when I did lspci. I'm really new to linux, so I'm having issues figuring out exactly what is wrong. Any help is greatly appreciated.:)

1. Did the sound card show up in the restricted drivers management?
2. Did you try "alsamixer"?

---

### Post by erginemr on 2008-03-21
This is the most strange thing, because Ensoniq ES1371 [AudioPCI-97] is a standard sound chip, I also have the same chip and my sound card (SB Vibra 128 with the same chipset) had worked out of the box.

So, I also believe that you should run alsamixer to make sure that your sound has not been muted. Do you happen to have a speaker icon at the top right of your desktop? If it looks as attached, then your sound should be working. 

Besides, did you check your speaker / monitor (if they are on your monitor) connections, and the sound settings of your speakers?

---

### Post by kwacka on 2008-03-21
Check, using something like gnome alsa mixer, that 'external amplifier' is not selected.

---

### Post by Computer Junkie on 2008-03-21
I have tried alsamixer, but I have no idea what I'm supposed to mute/unmute. Master is on, Master Mono is on, PCM is on, and IEC958 is on. Everything else is off. It shows the sound icon in the top bar. Under sound settings it is set up as Sound events : Sound playback : Autodetect, Movies and music: Sound playback : Autodetect, Audio Conferencing : sound playback : Auto Detect + Sound Capture : ALSA, Default Mixer Tracks : Device : Ensoniq Audio PCI (ALSA Mixer). I have tested the speakers and they work on my laptop, so I know it's not that. It seems like it really should be working right now.

---

### Post by billgoldberg on 2008-03-21
You guys might want to try:

gnome alsamixer (download from applications -> add/remove)

It will let you configure alsa from a gui, thus you can more easily tweak your sounds settings.

For me, I couldn't get my headphones to work using alsamixer because I couldn't select it. It work without a problem using gnome alsamicer.

---

### Post by Computer Junkie on 2008-03-21
> **billgoldberg said:**
> You guys might want to try:

gnome alsamixer (download from applications -> add/remove)

It will let you configure alsa from a gui, thus you can more easily tweak your sounds settings.

For me, I couldn't get my headphones to work using alsamixer because I couldn't select it. It work without a problem using gnome alsamicer.

I couldn't find gnome alsamixer anywhere on add/remove. Is it under a different name than that?

---

### Post by billgoldberg on 2008-03-21
> **Computer Junkie said:**
> I couldn't find gnome alsamixer anywhere on add/remove. Is it under a different name than that?
 
I find it, it might come from the medibuntu repo's, but I doubt that. It exact name is gnome alsamixer.

In the top right corner of add/remove, do you have it set to "all available applications"?

Edit:

the terminal command is 

```
sudo apt-get install gnome-alsamixer
```

---

### Post by Computer Junkie on 2008-03-21
> **Computer Junkie said:**
> I couldn't find gnome alsamixer anywhere on add/remove. Is it under a different name than that? Nevermind I found it, but it doesn't have any options that are different form regular alsamixer. Plus I get an error that says "An Error occured while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration properties may not work properly. Details are Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master_Mono": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master_Mono": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Center": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Center": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Depth": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Depth": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Line": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Line": '\320' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-CD": '\320' is

---

### Post by billgoldberg on 2008-03-21
I'm all out of ideas

---

### Post by Computer Junkie on 2008-03-21
> **billgoldberg said:**
> I'm all out of ideas lol thanks anyway...It might actually have something to do with my computer itself. I'd have to download a different OS to figure that out though. I don't want to leave Ubuntu! :sad:

---

### Post by erginemr on 2008-03-22
Can you please check whether you have sound when you boot from the Ubuntu Live CD?

---

### Post by CRISM on 2008-04-22
I just got my Ensoniq AudioPCI card working after nearly 2 weeks of trial and error. I also had no sound on my Ubuntu Gutsy Gibbon installation, and my lspci output was similar to yours. It appears that the problem is the ALSA sound driver which appears in the lspci listing as ES1371 and in other listings as snd-ens1371. My solution was to install OSS drivers on my system. Here's an outline of the steps I followed:

1) Go to [www.opensound.com](www.opensound.com)
2) Click on Download on the left side of the page. You will get a screen of logos.
3) Click on the Open Sound System logo.
4) Select the version to download. I chose linux 2.6 (x86) (TAR). Click Submit.
5) The next screen has the download link and also a link to installation instructions. You will need to follow the instructions on page 2 carefully. In particular, I had to make sure the downloaded package was in the root (/) directory, that I then changed to that directory before issuing the commands, and that I used the sudo instruction before each command to have root privileges.
6) On my system, I got error messages when I first tried to execute some of the commands. If you get these messages, read them carefully. They will tell you what other packages your system is missing that are needed before the installation can proceed. You will need to download and install those packages one at a time using....sudo apt-get install missing-pkg. You must substitute the name of any package listed in the error message in place of 'missing-pkg'.
7) Once all missing packages have been installed, go back and follow the installation instructions for the OSS drivers again. When successful, you should see a number of drivers being installed by name. In particular, I believe the audiopci driver is the one that works for the Ensoniq card.
You will have to restart after installation.

Now here's the tricky part. I still had no sound after all the above because it was somehow still using the ES1371 driver instead of my new driver. I went to the /etc/modprobe.d folder and then edited the blacklist file in that folder. At the bottom of the file, I added the line... blacklist snd-ens1371 and saved.

When I re-booted again, I got no sound during boot. But when I tried playing a .wav file, I had full stereo sound!! I still don't get sound during boot. Guess that's another problem. By the way, my lspci command now mentions OSS AudioPCI as the driver instead of ES1371.

---

### Post by erginemr on 2008-04-22
For the sound at boot, there are two locations you can check: 
Main Menu -> System -> Preferences -> Multimedia Systems Selector
Main Menu -> System -> Preferences -> Sound

In both, no reference should be made to ALSA, all should point to OSS. Try this, maybe you will have sound at boot this way.

---

### Post by erginemr on 2008-04-22
You may also consider giving ALSA another chance by upgrading it to ver. 1.0.16 by following:
[I][http://ubuntuforums.org/showpost.php?p=4582204&postcount=41](http://ubuntuforums.org/showpost.php?p=4582204&postcount=41)
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)[/I]

---

### Post by kwacka on 2008-04-22
Right-click on speaker icon in panel, select 'open volume control'

Click Edit --> preferences.

Scroll down, make sure 'External Amplifier' is selected. Click close.

Click 'switches', ensure that 'External amplifier' IS NOT selected.

I tore my hair out before I realised that, by default, this is set.

---

