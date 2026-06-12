---
title: "Earphones on laptop"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by archieanderson on 2007-04-14
I am completely new to Linux and have recently installed Ubuntu on my MSI laptop to see what it's like. Today I tried to use my earphones, but after I plugged them in the jack, the sound kept coming through the laptop's built-in speakers. I don't believe it's a bug, as I also have Windows Vista installed on the same laptop and had the same problem with that as well; Vista noticed that the phones were plugged in but didn't activate them automatically, so I had to set them up as the default output device in the Sounds settings. Also, according to Vista, the speakers are connected to an internal jack, as opposed to the external one that the earphones go into. Basically, I would like to get some help on how to check if Ubuntu can see my earphones, and how I can redirect the sound output to the external jack. Many thanks in advance.

---

### Post by nhandler on 2007-04-15
As far as I know, there is no way to tell if headphones are plugged in. You could try checking the sound levels. Maybe the sound level for the headphones is muted, or all the way down. You can get to the sound levels by either double clicking the speaker icon in the top panel (next to the clock), or typing 'alsamixer' into a terminal.

---

### Post by FuriousLettuce on 2007-04-15
Right click on the speaker icon on the top right, go to 'Open volume control'. Go to edit -> Preferences, and make sure the option 'Headphone Jack Sensor' is ticked. Press OK, then press the 'Switches' tab, and tick the 'Sense headphone jack' option, and then it will be fine :)

---

### Post by mdknaebel on 2007-04-15
On my laptop, I have to turn the 'Built-in Speaters" down and the "Master" up for sound to come thru the headphones only

---

### Post by archieanderson on 2007-04-15
Thanks for the responses, but unfortunately the phones still don't work. I tried the Preferences in Volume Control, but it doesn't have a Headphone Jack Sensor option :( The only switch I have 
is 'IEC958', which I have no idea what it does (Google landed me a definition "A standard for digital audio transfer published by the IEC (International Electrotechnical Commission), describes the protocol used by AES/EBU (now called AES3) and S/PDIF for transferring digital audio data between hardware platforms." -- if that's helpful for anyone...).

When I checked the settings in Volume Control, there was a Change Device submenu in File, with two options:
0 HDA Intel (Alsa Mixer)
1 Realtek ALC883 (OSS Mixer)

If I switch to Realtek, the Capture and Switches tabs disappear, but there's still no Jack Sensor in Prefs. The earphones just don't seem to appear in the mixer in any way, shape or form.

---

### Post by mdknaebel on 2007-04-15
on mine, the headphones do not appear on thier own "channel" but when the Laptop's built-in speakers are turned down with the master up, it comes thru the headphone jack.  This happens even without anything done to a headphone detection option.

---

