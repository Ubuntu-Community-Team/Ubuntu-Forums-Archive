---
title: "[SOLVED] Sound doesn't work in some apps while others run"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Roanoke on 2008-02-17
I have the problem that if I start up zynaddsubfx after firefox, zynaddsubfx sound doesn't work. If I do that in reverse, firefox sound doesn't work. I'm not sure what to do, does anyone have a clue? It should be noted that this is unique to zynaddsubfx.

---

### Post by Jewfro_Macabbi on 2008-02-17
Maybe you need to configure sound to shared?

---

### Post by Roanoke on 2008-02-17
How, exactly?

---

### Post by Jewfro_Macabbi on 2008-02-17
System - preferences - volume control - options

---

### Post by Roanoke on 2008-02-17
That's strange, I don't seem to have an options menu in the menus. I do, however, have a preferences menu, but that doesn't have anything about sharing sound cards.

---

### Post by Jewfro_Macabbi on 2008-02-18
Goto system - preferences - and select "volume control".  In the volume control panel - click on options - and check the surround jack mode. is it independent or shared?

---

### Post by Roanoke on 2008-02-18
I don't have anything about jack in the preferences menu. For reference purposes, I am going Edit -> Preferences in the volume control window.

---

### Post by Jewfro_Macabbi on 2008-02-18
It's under the options tab in the volume control menu

---

### Post by Roanoke on 2008-02-18
There is no options tab in Gutsy.

---

### Post by Jewfro_Macabbi on 2008-02-18
Sorry then - I'm not sure how to change it on Gutsy - but I thought I had remembered it being identical. Perhaps you could try installing alsamixergui if you are using alsa audio

---

### Post by Roanoke on 2008-02-18
Installed, now what?

---

### Post by Jewfro_Macabbi on 2008-02-19
It should be in your applications menu - under sound and video I think - try looking at it and seeing if it has some more advanced options. From the description of your problem - only one audio source can play at a time - it sounds like you need to find where to set your audio jack to shared.

Here's a good guide with info specific to your problem:

[https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

---

### Post by Roanoke on 2008-02-19
Thanks, it works now.

---

