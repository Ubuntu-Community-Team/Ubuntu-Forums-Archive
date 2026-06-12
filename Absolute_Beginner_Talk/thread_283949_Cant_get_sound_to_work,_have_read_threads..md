---
title: "Cant get sound to work, have read threads."
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2006-10-24
Ok, well heres the deal, theres a few things with sound i can get working, for one i have a SBAudigy 2 Value which linux recognizes and everything but, i cant get my logitech keyboard volume and mute control to work with the card, in the GNOME it does it if i select the default sound card, but when i change it to the SB the keyboard wont change it, also i cant get sound to come up on videos on the internet and on certain applications, any help?

---

### Post by TheNemeses on 2006-10-25
bump for good luck

---

### Post by Dr. Nick on 2006-10-25
So you have 2 soundcards? One onboard that you dont want and a add in that you do (sb audigy)?

My advice would be to go into the bios and disable the onboard one if thats the case, that may solve your problems.

I had similar issues of some stuff not working if I selected something other then the "default sound device" in the gnome prefrences, But disabling the onboard from the bios made my SB Live the default and it worked.

If you cant disable it in the bios then look into blacklisting the module that the undesired sound card uses

---

