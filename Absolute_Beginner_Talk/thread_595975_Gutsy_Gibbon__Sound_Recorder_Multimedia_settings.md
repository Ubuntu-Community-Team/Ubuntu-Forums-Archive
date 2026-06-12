---
title: "Gutsy Gibbon  Sound Recorder Multimedia settings"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ynottony on 2007-10-29
When I click on Sound Recorder in Gutsy Gibbon I get the following message:

"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

[LIST]
[*]Where are the Multimedia settings and how do I correct them?
[/LIST]
[LIST]
[*]I can record in Audacity, but cannot play back what I've recorded.  I can save the file and then click on the saved file and it will play fine.
[/LIST]
[LIST]
[*]The only way I can play back my recording is to open Audacity via "gksudo aoss audacity" and I can record and play back there, but cannot export to mp3.  When I click on find file for the encoder click on it, it doesn't load.
[/LIST]

I'm a newbie.  Would appreciate help on any of this.  Thanks.

- Tony Brigmon

---

### Post by Pumalite on 2007-10-29
System>Preferences>Removable Drives and Media>Multimedia

---

### Post by ynottony on 2007-10-29
Thank you.  Now that I'm in Multimedia, I see only the commands for Audio CD Disks, Video DVD Disks, and Portable Music Players.

[LIST]
[*]The command for Audio CD Disks is: [/sound-juicer -d %d
[/LIST]
[LIST]
[*]The command for Video DVD Disks is: totem %m
[/LIST]
[LIST]
[*]The command for Portable Music Players is:rhythmbox
[/LIST]

How would I know which audio capture settings are invalid. And how do I correct them in the Multimedia settings so I can use Sound Recorder?  Please advise.  Thank you.

- Tony Brigmon

---

### Post by ynottony on 2007-10-29
oops ...

The command forAudio CD Disks is: sound-juicer -d %d

I had a typo "[/sound-juicer -d %d" in my last post.

Again, not sure which audio settings are invalid or how to correct.

- Tony Brigmon

---

### Post by WhatTheCoitus on 2007-11-06
Hi ynottony,

You could try this...Top bar System > preferences > Sound. From here you can setup the default media options for your system.
i.e. Which hardware/sw device will be the default mic or audio etc. 

Then open the volume control via the top bar right > speaker icon...then Edit Preferences tick the box's for the Mic. Capture, Mic. +20dB, and Capture etc. Then Close.

Now you will have new tabs next to the playback tab in the main volume control GUI Recording Vol Control mutes. Switches 20db boost switch and any other relevant switches which change depending on your preferred settings.

Provided that you have the Media devices set correctly for your system devices the sound recorder should open. You can use Top bar System > Preferences > Hardware Information. to help narrow down the best options for device settings.

Good luck.   


EDIT: You may need to select the ALSA advanced for some settings I don't think that the sound capture has an auto detect option as you may not want what it selects.
If all looks well but the recorder wont open set the capture device to ALSA advanced. and see if it opens. .

---

