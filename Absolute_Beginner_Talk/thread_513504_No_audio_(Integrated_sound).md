---
title: "No audio? (Integrated sound)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Morph89 on 2007-07-30
Hey, I just started using Linux a few days ago and I'm loving it, there is just one problem that is  limiting it's full potential for me: I have no sound!

The speaker icon in the top right had a red x through it and a message said that an audio device could not be detected. In my PCI slot, I have a Creative X-Fi Soundblaster (Xtreme music) and I am aware that Creative has yet to deliver any X-Fi support for Linux via audio drivers. Before I could give up on this fantastic OS, I remembered that my motherboard, albeit 3-4 years old, still has an archaic integrated audio card. 

My motherboard is an nForce 2 (i don't know the manufacturer?) and I *believe* (from some googling) that the integrated audio card is a Realtek AC'97. Initially I had disabled this card via the BIOS, so I went ahead and reactivated it. Now when I boot up, the speaker icon has no red x on it. I go to play a .wav audio file through the rhythmbox music player and I still get no sound.

After reactivating the integrated sound card through the BIOS, I went into the sound configuration now I have options to use ALSA, N-Force 2, N-Force 2-IEC958, and some others. However, I was unable to get any sound from either of these configurations. Here's a pic:

[IMG]http://i202.photobucket.com/albums/aa106/Morph2007/audio.png[/IMG]

Any suggestions ideas would be much appreciated.

---

### Post by Redache on 2007-07-30
This may sound obvious but, have you removed the Creative from the computer?

This will cause an IRQ conflict, meaning sound will not work. 

Even so, the integrated sound should work.

---

### Post by compiledkernel on 2007-07-30
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by shagster_ on 2007-07-30
have you referenced this yet?
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

first thing everyone says is to make sure alsamixer doenst have any of your required channels/settings muted

---

### Post by anewguy on 2007-07-31
I'll pass along what works with the integrated sound in my laptop that in Windows uses Realtek.  I set it to ALSA in Ubuntu, but still no sound.  Then I found 1 post that mentioned something that worked, so maybe it's worth a try for you for your integrated sound:

open the ALSA mixer

click on Edit and Preferences

scroll down through the list and find "External Amplifier"  and check it

now exit from edit so you are back on the main ALSA mixer screen

click on the "Switches" tab

find "External Amplifier" and uncheck it here 


Seems counterintuitive - including external amplifier but turning it off, but it works!:)

---

### Post by Morph89 on 2007-08-01
> **anewguy said:**
> I'll pass along what works with the integrated sound in my laptop that in Windows uses Realtek.  I set it to ALSA in Ubuntu, but still no sound.  Then I found 1 post that mentioned something that worked, so maybe it's worth a try for you for your integrated sound:

open the ALSA mixer

click on Edit and Preferences

scroll down through the list and find "External Amplifier"  and check it

now exit from edit so you are back on the main ALSA mixer screen

click on the "Switches" tab

find "External Amplifier" and uncheck it here 


Seems counterintuitive - including external amplifier but turning it off, but it works!:)

Hey, I tried following your instructions, but I cannot find this "Edit > Preferences" you're talking about. When I load the alsa mixer, I get this:
[IMG]http://i202.photobucket.com/albums/aa106/Morph2007/alsa.png[/IMG]

Perhaps there is a step I am missing?

As for everyone else, I've tried nearly all of the online guides and I'm still getting no sound :-/

---

### Post by anewguy on 2007-08-01
Ooops - maybe I gave it the wrong name - I just double click on the speaker icon on my task bar.  I think it is actually called the volume control?  At any rate, if I can figure out how to put a captured screen image here, I'll post it!:)

---

### Post by cookies on 2007-08-01
> **anewguy said:**
> Ooops - maybe I gave it the wrong name - I just double click on the speaker icon on my task bar.  I think it is actually called the volume control?  At any rate, if I can figure out how to put a captured screen image here, I'll post it!:)


Applications > Accesories > Take Screenshot

>_>

Anyway, since I'm not good with sound, I'm just here to say that.

---

### Post by jnorthr on 2007-08-01
Just had the same problem this morning. The alsamixer (on my machine) opens in the gedit text editor tool, so it can be mis-leaing that the toolbar menu items are NOT for alsamixer. The only real keys that seem to work are the arrow keys : left & right to choose the column to the left or right, the up/down arrow keys to raise or lower the sound level within the current channel, the 'space bar' to activate or de-activate that column's function and the 'm' key which mutes the currently active feature. Then escape key to save the config. Then back to Appl.>Sounds>Recorder (etc.) tool to work on muli-media. 

your screenshot shows several columns with MM ath the bottom of the column. Press the 'M' key to turn off/on the mute feature then try again.

BTW: I have had no success getting any sounds out of rythembox yet despite all my efforts.. 8-P

---

### Post by Cappy on 2007-08-01
You can ```
lspci | grep audio
``` if that doesn't bring up anything you can ```
lspci
``` and find your audio driver in that list.

On your playback you need the control called "PCM" turned up .. that's probably your audio output.

Double click on your speaker at the top right hand corner. Edit-->Preferences
Check everything off. Turn PCM up on the Playback tab. You may need to goto the Switches Tab and uncheck "External Amplifier" or something.

---

### Post by anewguy on 2007-08-01
> **cookies said:**
> Applications > Accesories > Take Screenshot

>_>

Anyway, since I'm not good with sound, I'm just here to say that.

Got the take screenshot current window figured out , what I don't know is how to paste it here.  It seems to want a URL, and I have no where to post the picture so I can include it here.  I've tried Shutterbug, but I can never figure out what the URL to a specific picture is.  Any ideas?:)

---

### Post by anewguy on 2007-08-01
I may have found the link to my snapshot and I guess it's Shutterfly, not Shutterbug!:)

[IMG]http://im1.shutterfly.com/procserv/47b7d620b3127cceb82f49c1655400000000100AZs2rJk5ZN2Kg[/URL][/IMG]

Edit:  apparently even though I have the URL, Shutterfly won't give access to it, so it doesn't show.

---

### Post by anewguy on 2007-08-01
Let me try one more time:

[ATTACH]39557[/ATTACH]

---

