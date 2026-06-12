---
title: "Sound -- Access Denied ??"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by tarpon_bill on 2006-12-27
I have been trouble shooting no sound on an edgy new install. When I do the command lspci -v in a terminal, the on-board sound chip is found but 'access denied' shows in the capabilities section. The chip is an Intel AC '97 82801.

The bios has sound enabled, no muted channels, but not a peep.

Been looking through the alsa website and no help for my problem found.
 
Anyone care to take a shot?

---

### Post by cptjaben on 2006-12-27
hmm, well when I type in the terminal: ```
lspci -v
```i get access denied under the 'capabilities' field, however when I type ```
sudo lspci -v
``` I don't and i can see the 'capabilities' field. I don't know if this is the same thing that's happening to you. Also, I really have no idea whether or not this will fix your problem, but have you made sure the master sound control is turned up on your alsa mixer. To check, type in the terminal ```
alsamixer
``` and use the arrow keys to make sure the 'master' field is turned all the way up. Hope this helps.

---

### Post by tarpon_bill on 2006-12-27
sudo lspci -v does indeed produce an output, at least for me. It changes from access denied, to '[50] power management version 2' so that likely isn't causing the sound problem. False alarm ... my bad.

alsamixer shows volume at max and mute off, so if the sound was there it should get through.

The system is a dual boot attempt with win XP where the sound works fine.

....

Another anomaly sudo lspci -v ..
In the multimedia section, there is a line which includes "Unknown device 5790". I can't find this device anywhere in alsa driver data.

Any other tests I might try??

---

### Post by cptjaben on 2006-12-27
Do you have more than one sound card i.e. one built in to your motherboard and one pci one? if so, when you look at the sound section in preferences (system>preferences>sound). is default sound card the one you want to use?

---

### Post by tarpon_bill on 2006-12-27
No, only one sound system, there is just the motherboard sound chip.

---

