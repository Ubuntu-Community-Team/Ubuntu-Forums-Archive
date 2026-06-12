---
title: "No Sound on new MBP"
date: 2010-10-07
forum: Apple Hardware Users
---

### Post by michelex on 2010-10-07
Hello All, 

I have installed Ubuntu 10.04 in MBP that I bought a month ago. I found it easier to install it using the bootcamp through OSX. Ubuntu works well. Nearly everything worked out of the box except the brightness keys and the sound/microphone. I am able to adjust the sound level using the keyboard keys (F10 - F12). However there is no sound. Skype also does not detect a microphone. I searched on the web and found the following instructions: 

[https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sensors](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sensors)

They did not work either. So please help. 

Thanks, 

Michele

---

### Post by michelex on 2010-10-08
Found the solution on this forum by dngfng given below: 

Managed to fix it.

Just in case anybody else is facing a similar issue.

Install alsamixer 
Start alsamixer from command line and unmute the muted channels by pressing "m" on the muted channel.

I am not sure why this is the case - strikes me as odd that by default  the speaker channels are muted and you can't unmute them over the GUI.

Does anybody have an idea as to why this is the case?

-------

I would like to add one more thing here. Make sure you unmute the front speakers.

---

