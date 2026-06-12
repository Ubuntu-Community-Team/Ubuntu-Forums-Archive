---
title: "Microphone Does NOT record! Help!"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-30
Hello!

Yesterday I bought a new **microphone** for my other PC.
For an **Asus P5LD2 Mobo**:
You can find its specs here: [http://uk.asus.com/products4.aspx?l1=3&l2=11&l3=185&model=515&modelmenu=1](http://uk.asus.com/products4.aspx?l1=3&l2=11&l3=185&model=515&modelmenu=1)

I checked the Mic on another PC & it works fine!
So, the mic is NOT the issue here...

I used the Terminal, checked "[color=blue]alsamixer[/color]", nothing is muted, all mics are in 100% volume levels...
Everything looks fine!
But when I try to record Sound, I can't listen anything!!!

_Note_:
It is funny, but when I test the mic outside the "[color=blue]Applications\Sound & Video\Sound Recorder[/color]" panel, I can hear my voice on the Speakers!!!

The Mobo uses:

1. Intel High Definition audio (HD Audio)
2. Realtec ALC 882 7.1 channel audio CODEC

Because of the above 2, when I launch "Applications\Sound & Video\Sound Recorder" & select "[color=blue]File\Open Volume Control[/color]", under "[color=blue]File\Change Device\[/color]", I am given 2 options:

1. HDA Intel (Alsa Mixer)
2. Realtek ALC882 (OSS Mixer)

I have tried out both, but NONE seems to work!

I also used the "[color=blue]Edit\Preferences[/color]" & have activated _every_ check box in there...

I have tried everything...
**I think that I need to install some Audio Drivers...**
Any idea which ones?
Can somebody guide me in this?

Thanks.

---

### Post by deadgobby on 2007-01-30
have you tried Audacity? If not install it by via Synaptic. Once Audacity is installed. Open it up, and you'll see a couple of mic icons. Click on the record button and see if it captures some audio.
Gobby

---

### Post by mikewhatever on 2007-01-30
Had a similar problem a while before. A forum member to solve it, by helping to install a newer alsa driver. See the thread [http://ubuntuforums.org/showthread.php?t=258878&page=2](http://ubuntuforums.org/showthread.php?t=258878&page=2)
In alsamixer, hitting Tab several times shows more options, at least in my case.
Lastly, to stop hearing my own voice, I had to mute Mic Bypass under Capture Tab in volume controls.

---

### Post by dvarsam on 2007-01-31
Hello & thanks for your reply!

[QUOTE=deadgobby]have you tried Audacity? If not install it by via Synaptic. Once Audacity is installed. Open it up, and you'll see a couple of mic icons. Click on the record button and see if it captures some audio.[/QUOTE]

I installed "audacity", but I could NOT record from the mic!
I will also try to install the drivers user "mikewhatever" suggested & get back to inform you.

Thanks.

P.S.> If you still have some other suggestion to make, please tell me... Thanks.

---

### Post by euchrid on 2007-06-07
Updating Alsa drivers worked for me. I posted my experiences and instructions here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Did you get yours working?

---

### Post by Keymone on 2007-08-03
i have similar problem and fighting with sound system for few days!

can somebody explain me how to check what soundcard do i have and where do i get the drivers?

it is really the point where all windows users say linux sux. and linux does sux here..

i have asus p5ld2 mb, i did compiled and installed alsa drivers, i did run alsaconf few times and i did reboot my computer each 10 minutes (i've heard linux does not need any reboot at all, why it is so hard to switch the modules without rebooting?)

sound is working OK on OSS but when i try to use ALSA in Amarok xine is dying with error message.

and micro is not working too.

please help somebody!

---

### Post by pavel989 on 2007-08-14
ive been having the same problem. when i talk into my microphone, the sounds goes out onto the speaker but no program will record. i have reinstalled alsa, tried audacity but nothing worked!!!

---

