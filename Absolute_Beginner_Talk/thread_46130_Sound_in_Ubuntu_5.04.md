---
title: "Sound in Ubuntu 5.04"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by newbie2006 on 2005-07-03
I am a beginner using Ubuntu 5.04. I downloaded Ubuntu and installed it in my computer which already had XP. I don't hear any sound from the speakers. I went through ubuntu guide and followed step to configure sound in gnome(Trouble shooting part). Everything is installed. I have a SOYO motherboard and an onboard audio chip. I looked at the manufacturer's website for the driver in LInux and they referred to alsamixer 1.08 (WHICH IS ALREADY IN 5.04). I can see Alsamixer 1.08. I can see that the bars move up and down when i play a song in XMMS but no sound through speaker:(

Can anybody tell me what might be the problem???

---

### Post by newbie2006 on 2005-07-03
Forgot to mention that i do hear sound when i go to XP at boot. XP sucks..Ubuntu rocks!!!(except without sound for now..)

---

### Post by manicka on 2005-07-03
Maybe a a silly suggestion. Have you checked the volume controls using the volume control manager in the toolbar (right click and choose open volume control) and that sounds are turned on in the system preferences, System-->Preferences-->Sound

You might also need to choose a different output sink to suit you setup. You can choose different output sinks and test them using, System-->Preferences-->Multimedia Systems Selector

---

### Post by Kyral on 2005-07-03
Soundcard and Onboard?

This is the one thing that is really a b***h in Linux. I have a soundcard and onboard as well, and the only way I got Linux to use the soundcard is (before installing Ubuntu) was to go into the BIOS and disable the onboard sound. Then Linux liked my soundcard

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=Kyral]
This is the one thing that is really a b***h in Linux. I have a soundcard and onboard as well, and the only way I got Linux to use the soundcard is (before installing Ubuntu) was to go into the BIOS and disable the onboard sound. Then Linux liked my soundcard[/QUOTE]

This post is wise. Currently Ubuntu has some sound problems. The developers are working hard to fix this stuff in the next release. Till then...

---

### Post by filemanager on 2005-07-11
[QUOTE=Kyral]Soundcard and Onboard?

This is the one thing that is really a b***h in Linux. I have a soundcard and onboard as well, and the only way I got Linux to use the soundcard is (before installing Ubuntu) was to go into the BIOS and disable the onboard sound. Then Linux liked my soundcard[/QUOTE]
 My sound doesn't work whether the BIOS onboard sound is enabled or disabled, doesn't work either way.

I don't think alsa is installed properly on my machine. If I type "alsamixer" in the terminal it says "file does not exist or cannot be found". Is there a way to make sure it's installed properly?

---

### Post by GrootBrak on 2005-07-12
Yah. Hear what you say. Downloaded my drivers from Intel for sound and graphics. Both won't install, and I've read the guides, got everything as asked for in the guides, but come to install some package or the other is missing. I've given up, and hopefully I will recieve a new copy of the Ubuntu CD. With luck it will resolve itself.

BTW. My volume control drop back to zero if I try and increase the volume. Oh and video clips won't play at all. The only "multumedia" I have is my display is working, but not to my satisfaction and not with the Intel drivers. (Pure white seems grey, in fact everything seems too dark.)

---

### Post by UbuWu on 2005-07-12
A lot of people have problems with sound on hoary. Here you can find some useful howto's:

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

And about using two soundcards:

[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

### Post by filemanager on 2005-07-12
[QUOTE=UbuWu]A lot of people have problems with sound on hoary. Here you can find some useful howto's:

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

And about using two soundcards:

[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)[/QUOTE]
 It seems like almost everyone is having sound problems!

What I need an answer to is why when I type "alsamixer" which everyone tells me to do, it says "file cannot be found" =\

---

### Post by UbuWu on 2005-07-12
[QUOTE=filemanager]It seems like almost everyone is having sound problems!

What I need an answer to is why when I type "alsamixer" which everyone tells me to do, it says "file cannot be found" =\[/QUOTE]

Install alsa-utils with synaptic or 'sudo apt-get install alsa-utils'

---

### Post by filemanager on 2005-07-12
[QUOTE=UbuWu]Install alsa-utils with synaptic or 'sudo apt-get install alsa-utils'[/QUOTE]
 It's already installed, I re-installed it via Synaptic but I still get the "command not found" thing when I type "alsamixer" or "gnome-alsamixer" in a terminal =\

---

### Post by UbuWu on 2005-07-12
[QUOTE=filemanager]It's already installed, I re-installed it via Synaptic but I still get the "command not found" thing when I type "alsamixer" or "gnome-alsamixer" in a terminal =\[/QUOTE]

And what if you try /usr/bin/alsamixer ?

---

### Post by filemanager on 2005-07-12
[QUOTE=UbuWu]And what if you try /usr/bin/alsamixer ?[/QUOTE]
 alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by arunsub on 2005-07-12
Go to 
application - sound and video - volume control
File - change device  and select the right entry(for your sound card) there. After you select the entry, check the volume is not muted. 

Also check
system - preference - multimedia system selecter and select OSS if alsa doesnt work. Select one by one and see if you get the sound.

---

### Post by filemanager on 2005-07-12
[QUOTE=arunsub]Go to 
application - sound and video - volume control
File - change device  and select the right entry(for your sound card) there. After you select the entry, check the volume is not muted. 

Also check
system - preference - multimedia system selecter and select OSS if alsa doesnt work. Select one by one and see if you get the sound.[/QUOTE]
 I can't open volume control. When I do it says "No Volume Control elements and/or devices found"

---

### Post by arunsub on 2005-07-12
[QUOTE=filemanager]I can't open volume control. When I do it says "No Volume Control elements and/or devices found"[/QUOTE]
Reinstall Ubuntu.  :smile: 
Sorry, I don't know what the problem is then.

---

### Post by filemanager on 2005-07-12
[QUOTE=arunsub]Reinstall Ubuntu.  :smile: 
Sorry, I don't know what the problem is then.[/QUOTE]
 Already did that 4 times!

---

### Post by UbuWu on 2005-07-12
[QUOTE=filemanager]Already did that 4 times![/QUOTE]

Looks like the soundcard isn't detected. What soundcard do you have? Is it listed when you type lspci at the command line?

---

### Post by filemanager on 2005-07-12
[QUOTE=UbuWu]Looks like the soundcard isn't detected. What soundcard do you have? Is it listed when you type lspci at the command line?[/QUOTE]
 I have a Sound Blaster Live! 24-bit sound card.

lspci gives me this:

> 
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0282
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1282
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2282
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3282
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4282
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7282
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)



---

### Post by mookie2125 on 2005-07-13
Hi  - with one and a half days under my belt having loaded v4.10
I've just gone through a similar effort , however I went way too deep into files 
folders etc,  sylslog - no errors but still no sound.
Eventually tracked the problem down to the Volume Control Panel 
Applications>Mutimedia>Volume Contol
I have a C-Media Cobra sound card with a C-Media 8738 chip (active)
and onboard (AC97) sound driver disabled in BIOS.
My Panel comes up with 2 options at the top of it
 C-Media PCI [OSS Mixer] and C-Media PCI 8738 [Alsa Mixer]
with the oss mixer selected the panel is truncated
with the [alsa mixer] active you can scroll to the right
I found that unchecking the mute box labelled  IEC 958 In-Monitor 
restored sound. NOTE these extra controls are not visible unless the alsamixer is selected.
I have no idea what your Volume Control Panel looks like, however if it has the ALSA 
MIXER try unchecking that box
Good Luck

---

### Post by filemanager on 2005-07-13
[QUOTE=mookie2125]Hi  - with one and a half days under my belt having loaded v4.10
I've just gone through a similar effort , however I went way too deep into files 
folders etc,  sylslog - no errors but still no sound.
Eventually tracked the problem down to the Volume Control Panel 
Applications>Mutimedia>Volume Contol
I have a C-Media Cobra sound card with a C-Media 8738 chip (active)
and onboard (AC97) sound driver disabled in BIOS.
My Panel comes up with 2 options at the top of it
 C-Media PCI [OSS Mixer] and C-Media PCI 8738 [Alsa Mixer]
with the oss mixer selected the panel is truncated
with the [alsa mixer] active you can scroll to the right
I found that unchecking the mute box labelled  IEC 958 In-Monitor 
restored sound. NOTE these extra controls are not visible unless the alsamixer is selected.
I have no idea what your Volume Control Panel looks like, however if it has the ALSA 
MIXER try unchecking that box
Good Luck[/QUOTE]
 I can't open Volume Control. I get a "No volume control elements and/or devices found" error.

---

### Post by mookie2125 on 2005-07-13
Hi
The volume control panel display is a function of the "gnome desktop" 
The display is based on what soundcard you have installed as sensed by Gnome.

Do you know what audio chip is on the motherboard , if you have documentaion for your  M/B  you may be able to find out what chip is used for the "on-board audio"
if not are you familiar with the insides of your computer? 
Are you comfortable in accessing the inside of your computer to find the audio chip on the M/B to identify it? 
If you can identify it from one of the means above ( or from your search regarding soyo M/B's) now follow this path which should show up whether your audio driver/chip is recognized.
From COMPUTER>disks>filesystem>user>share>alsa>cards.
scroll through the drivers listed in "cards"  after you open the folder.
If it is not there you need to positively identify the chip and locate a linux compatible driver for it. try google etc, also try linuxquestions.org and do a search , you may find the info you need.
good luck
rgds

---

### Post by UbuWu on 2005-07-13
[QUOTE=filemanager]I have a Sound Blaster Live! 24-bit sound card.
[/QUOTE]

This one is known to have problems, because it uses software mixing instead of hardware mixing, which means that your pc's processor mixes sound instead of the soundcard itself. I don't know how to get it to work, but if you search the forums you will find more on it.

---

### Post by mookie2125 on 2005-07-13
Looking in "cards" folder my cmptr shows "audigy"  and "audigy 2" drivers already available " loaded in the defalt loading of Ubuntu."  Not sure if this is the same as audigy live. it also shows that it uses EMU10K1 chip for both configurations.
Folder Alsa-Base -(OSS-List)  would appear to list all the useable cards/drivers
Maybe the card installed uses an emulator such as the EMU10K1.
If you have on board sound, then deactivate the add-on card in bios at start up and plug speaker connection into the mainboard speaker outlet for evaluation.
don't forget to reset all the volume settings.
check if "applications>mutimedia>volume control
now displays volume panel.
If it does,  uncheck all the mute boxes one by one in "alsa-mixer" until sound is available. 
let's see what happens
Rgds

---

### Post by lol on 2005-07-19
What is really missing in Ubuntu is "alsaconf". If you have trouble with alsa, you can try to download the Debian version of alsa-utils ([http://www.debian.org/distrib/packages)](http://www.debian.org/distrib/packages)), unpack it and copy alsaconf in a safe place, then run it. It's not going to solve all alsa related issues, but it may help. I used it successfully with a SB Live.

My only remaining problem now is that the mixer settings keep being reset (everything is muted) each time I reboot. I still haven't figured out why, but I am working on it...

A simple way to verify that alsa is correctly setup for your sound card is to check that at least the correct modules are loaded. 'lsmod' should give you something like this (depending on your sound card):
snd_emu10k1            98116  2
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  4 snd_bt87x,snd_emu10k1,snd_ac97_codec,snd_pcm_osssd_mod                 17872  0
... (there is more)

Hope this can help a bit.

---

### Post by GrootBrak on 2005-07-20
I still have'nt heard squeek from Ubuntu. I even downloaded the driver from Intel and installed it according to their wims, but almost right in the end I have to do a "Make" and there is no "Make" found an error in Intel's manual, I supposed it was a typo, but even that won't work. I have the ALSA drivers as well, but I Azalia is what Intel want. Hopefully I will recieve some enlightenment in future. 


(Nah. I prefer sound over light...)

---

