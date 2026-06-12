---
title: "Sound is not working."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-04-23
I use a headset and mic for sound, but it doesn't seem to be working.  It works fine on my windows partition.  Any suggestions?

---

### Post by IgnacioMiller on 2007-04-23
Type 'alsamixer' in the command line. Are all of the correct channels unmuted and up to a sufficient volume?

---

### Post by PleaseEnjoyThis on 2007-04-23
I turned everything all the way up, but still no sound.  It even detects my sound card.  Hmmm :/

---

### Post by PleaseEnjoyThis on 2007-04-23
When I tried saving my changes this came up...

fer:~$ alsactl store 0
alsactl: save_state:1280: Cannot open /var/lib/alsa/asound.state for writing


HELP!

---

### Post by NoTiG on 2007-04-23
Is your headset USB ? if it is please merge this thread with this one: [http://ubuntuforums.org/showthread.php?t=419166](http://ubuntuforums.org/showthread.php?t=419166)

some others are having problems too

---

### Post by PleaseEnjoyThis on 2007-04-23
Their problem does seem to be similar, but is still not worked out.  They even have the same headset as me.  But in my sound preferences I don't even have the option of choosing USB audio.  

uuuugh....

---

### Post by NoTiG on 2007-04-23
if you type lsusb in the console it doesnt' show up?

---

### Post by PleaseEnjoyThis on 2007-04-23
Bus 002 Device 003: ID 046d:c041 Logitech, Inc. 

so I guess so.

---

### Post by NoTiG on 2007-04-23
I have the same exact device ID. it's weird that mine would at least detect them and yours wouldn't. I can play the test sounds but sound in general does not work.

i will let you know if i fix it somehow

---

### Post by PleaseEnjoyThis on 2007-04-23
My test sounds don't even work.  I hope to hear back from you.

---

### Post by NoTiG on 2007-04-24
shameless bump. and i plan to merge these threads once i find more people with this problem. So far there is 4 (including me)

[http://ubuntuforums.org/showthread.php?p=2521590#post2521590](http://ubuntuforums.org/showthread.php?p=2521590#post2521590)

---

### Post by PleaseEnjoyThis on 2007-04-24
Anyone know anything about this?!?!?!?!?

---

### Post by NoTiG on 2007-04-26
well i am going to try to compile the newest custom kernel to see if its been fixed upstream later

---

### Post by PleaseEnjoyThis on 2007-04-26
This guy saved my life.  I have never fully appreciated sound until now.  [http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by NoTiG on 2007-04-26
it worked! thanks

---

