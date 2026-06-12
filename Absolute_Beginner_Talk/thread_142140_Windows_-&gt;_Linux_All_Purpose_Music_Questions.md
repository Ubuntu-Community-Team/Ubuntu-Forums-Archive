---
title: "Windows -&gt; Linux: All Purpose Music Questions"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-09
1. What program can i use to transfer music/videos/podcasts to my 5th generation video ipod. gtkpod currently in breezy doesn't work, and i have tried a developmental version and keep getting unable to read Itunes.DB. YamiPod is rediculously unstable and lethargic. Any Suggestions?

2. Itunes music pruchases...  holy hell.  I have downloaded probably 1000 worth of songs in the past year in Itunes, I would really like to play these in linux, especially since i dont have Windows, and music is one of biggest uses of a computer to me.  Any Suggestions?

3. DAAP shares... I have downloaded a backport of rhythmbox which lets me play off shares with ease, being able to input passwords when needed to.  But how can I download such files to my computer (files which were first downloaded from me but I have since lost because of the removal of windows).  I can use ourtunes with java, and it works perfectly, except there is no way to put in a password (that i know of).  ANy Suggestions?

Thank you.

I am suprised Apple doesn't make Itunes for linux, i wonder how come?

---

### Post by HokeyFry on 2006-03-09
if you have access to windows on your computer then i can help you convert your songs mp3s. go to itunes, highlight all of your protected aacs. right click, then click convert selection to mp3, or whatever it says. Sit tight, wait for it to finish. Now, go to linux. I assume you can access your windows drive in linux. if you desire to, copy all of your mp3s to your linux drive/partition. Go to synaptic and download the gstreamer-mad plugin. Then add your newly created files to your favorite music player library.

As far as your ipod goes. Rythmbox should play the songs (make sure you have gstreamer-faad installed if you have unprotected aacs on it) and that should play them. You also said that gtkpod says it cant find the itunes DB. Well, i always got that, and it spent about 5 minutes looking at all of my songs. then i could manage them. However, my experience with gtkpod tells me that it will mess with your playlist orders and album song orders. I do not recommend gtkpod unless it is a last resort. I would recommend banshee, which is supposed to hae decent ipod support, but I have trouble getting it to work with mine. I have concluded that it needs an upgraded file that is unavailable for Breezy, but will be available for Dapper, some version of SDL or libsdl or something. But that could just be me. I suggest trying out banshee. even if it doesnt work, i like it so much i use it as my main music player now!

I dont even know what DAAP is so i wont even try to explain it.

And apple wont do itunes for linux because apple does not like linux, despite the fact that they have taken several ideas from it. Also, the linux itunes fans are not numerous enough for apple to make a version for linux.

---

