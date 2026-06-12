---
title: "Distored Sound - edgy"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by stalkier on 2007-03-01
Hello I have a Compaq Presario v2508WM laptop running dual-boot XP pro/ edgy eft. I have one problem other than the occasional WiFi lose (Broadcom). I have distorted sound using XMMS player for my MP3s. Does anyone have any idea how  can fix this? It didn't use to be distorted at first install. Thanks for the help.

PS - I believe I an using the VIA chipset.

---

### Post by Dr. Nick on 2007-03-01
Try changing the volume levels, I tend to get distortion if I max the system/player volume levels, Set them down and raise the speaker volume to compensate and see if its better

---

### Post by nudnik on 2007-03-02
> **stalkier said:**
> Hello I have a Compaq Presario v2508WM laptop running dual-boot XP pro/ edgy eft. I have one problem other than the occasional WiFi lose (Broadcom). I have distorted sound using XMMS player for my MP3s. Does anyone have any idea how  can fix this? It didn't use to be distorted at first install. Thanks for the help.

PS - I believe I an using the VIA chipset.

Make sure alsamixergui is installed so you can easily manipulate the audio on your PC. If not installed, open the terminal and type the following:

sudo apt-get install alsamixergui

Once installed you should be able to access it by clicking on the applications tab in the upper left hand corner of the Gnome screen (assuming you use Gnome). It will be located under Sound and Video, and should be either near or at the very top. Once activated, you can diddle with the Master and PCM settings until your sound is as good as possible. 

Keep in mind, the sound under Linux isnt always comparable to what you might get with XP. 
I had a 945PSN board (Intel chipset) which always produced a canned sound with a bit of a ring to it no matter which distro I tried. No such problems with XP. When using a board with AC97 sound, however, there isnt much difference.

---

### Post by stalkier on 2007-03-05
Thanks guys I will give these a try. (And who said MS tech support was better than Ubuntu forums??...... Must have been Gate's)

---

