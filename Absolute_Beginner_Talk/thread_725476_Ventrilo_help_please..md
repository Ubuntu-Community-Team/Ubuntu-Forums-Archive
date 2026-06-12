---
title: "Ventrilo help please."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by robinms on 2008-03-15
I guess everybody is tired of every single one who can't get ventrilo to work. Well, I'm one of those to. 

I have read through all "howto's", but I really don't understand so much. My friend got me in to this system, and I really like the whole thing, but I like to game alot, and I really need ventrilo for my raiding in WoW, which works great by the way.

If any one could tell me, from the start, how to get ventrilo 2.0.3 to work.
I'm a noobie in Ubuntu, so please be patient. 

Thanks!

Robin.

---

### Post by jprophet420 on 2008-03-15
well, i can help you on the first step, because thats where I am.

$apt-get install wine

This will get you wine, the windows emulator. Follow the propmts.

Then download the ventrilo installer. Once you get that done find the icon and right click on it. "Open with Wine" or something similar should be an option. It will open and install as if it were windows.

The problem I have is im not sure how the sound card needs to be configured. The codecs are missing and I'm not sure if thats whats holding me up or if I have to emulate the windows sound card drivers or not.

---

### Post by jprophet420 on 2008-03-17
found the fix. I hope i was concise enough on the install, here is the fix for the codec once installed:
[http://ubuntuforums.org/showthread.php?t=720774](http://ubuntuforums.org/showthread.php?t=720774)

---

### Post by tikigodbob on 2008-03-19
I'm gonna piggy back on to your thread, since vent is a common problem issue i think.

My ventrilo works fine, i can hear everything, but i can't speak. i often get an error telling me something else is using the input device already? which i don't understand, and other errors like hr 80004005, and i've tried multiple things to fix this, but i just can't seem to find any sort of solution.

i have a realtek ACL 888 audio card, if that makes a difference.

---

