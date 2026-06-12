---
title: "Space Bar doesn't work when Visual Effects are on!"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by michaelpagz on 2007-11-18
I just got gutsy. i love it. it erased berryl which i had on feisty fawn. i looked up how to get visual effects on gutsy and typed this in the terminal:```
sudo apt-get install compizconfig-settings-manager
``` which gave me the CompizConfig Setting Manager. Now heres the issue, when i select custom preferences in appearance preferences to get visual effects my space bar works randomly. When it doesn't work, I can hit Shift+Space Bar and it works fine. I know it has something to do with the Custom Preferences because it works perfectly (like now) when I select " none"  in Appearance Preferences. Is this a bug? Is there a fix? 
Please Help. and thanks  by the way. I've learned a great deal on this forum.

ps.I have a feeling theres a lot of bugs with Visual Effects because I can't get most of them to work anyway. but I always assume its me not doing something right.

---

### Post by stido on 2007-11-19
the cause might also be:
accidentally setting <spacebar> as an action keybinding is ccsm. try checking the Actions tab in ccsm.

---

### Post by michaelpagz on 2007-11-20
holy smokes it worked. thanks so much for your help!

---

### Post by dragonSBF on 2008-02-07
I had this exact same problem after a dist-uprade.  I just went through my ccsm of all my check mods and found that my Rotate Cube had mapped my SPACE button to Rotate Flip Left.  Needless to say I disabled/or give another hot key and it works just fine now with all my desired visuals.  Hope that helps? =\

---

