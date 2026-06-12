---
title: "before I ninstall Audigy 2"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by RDUBBALO on 2007-02-25
Before I install the Creative Audigy 2 sound card is there anything I should Know or do. I dont want it to have any conflicts and install properly? I checked the alsa site. Im thinking i will need the drivers and utilities. Any ideas would be helpful

---

### Post by Quintin Riis on 2007-02-26
Creative Labs stuff is generally well supported.

Just power down, put the card in, power up.

This might give you two sound devices if your system board has integrated audio.  If this is not desirable, disable the onboard audio in your BIOS or add the module for it to a blacklist.

---

### Post by Daveth on 2007-02-26
yes, works just fine when you power up. Load up gnome alsa mixer from synaptic in case you get stereo and you want 5.1 (worked for me) but otherwise it runs straight out of the box.

---

