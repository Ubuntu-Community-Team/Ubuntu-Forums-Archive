---
title: "[SOLVED] No sound, again, on Acer Aspire 5052"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by sahra on 2007-09-08
Hello.  I installed Ubuntu Feisty Fawn around a month ago on my brand-new Acer Aspire 5052AWXMi.  Sound wasn't working, so I went through the helpful advice on  [http://ubuntuforums.org/showthread.php?t=457011](http://ubuntuforums.org/showthread.php?t=457011).  I ended up doing a manual install of alsamixer; this proved to be difficult, but the useful steps given in the post on this forum resulted in me having sound.  Sound that didn't work entirely properly, but enough sound to get by temporarily.

However, after a recent update I was told to restart my system.  Upon having done so, I no longer have any sound at all.  When I click on volume control in my panel, I get an error saying "No volume control GStreamer plugins and/or devices found."  If I go to System -> Preferences -> Sound, I no longer have a device listed.  Trying to get into alsamixer via terminal says there is no such device.  Doing the command of 'aplay -l' in a terminal results in an error of "aplay: device_list:222: no soundcards found..."  The audio device in lspci says "00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)", though, and isn't that my soundcard?

I have to admit that I'm immensely frustrated by this, since I spent many hours the first time getting sound working to the minimum standard that I require and unlike the myriad of other problems I've experienced since my install, sound is really the one thing that has got to get working and not suddenly stop doing so right before *I* need to work. 

Can someone please help?  I'd very much appreciate if it could be understood that I'm a beginner on Ubuntu, and although I'm not a complete beginner on Linux, I haven't run a modern Linux as an end-user all by myself before -- so please spell out exactly what I need to do for any fixes as I have some odd holes in my knowledge.  Thank you so much!

---

### Post by sahra on 2007-09-10
Replying to my own post -- after many hours spent on the problem, I've managed to solve it.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) worked for my type of sound card; I assume there are other how-to's available for others.

---

### Post by fujaru on 2007-11-06
hi, I have acer aspire 5052 too. I could easily solve the sound problem by raising the 'SURROUND' volume meter in the volume control up or unmute it.

---

### Post by sahra on 2007-11-08
Please re-read the initial post to this thread and the solution that I found.  The "sound problem" you are mentioning is a minor bug; it is not the problem I had (or indeed the problem many people, on Acer brand or not, seem to have with alsamixer sound and updating of programs).

---

