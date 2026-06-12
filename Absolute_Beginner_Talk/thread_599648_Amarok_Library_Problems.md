---
title: "Amarok Library Problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-01
m quite new to Ubuntu and Amarok, so bear with me. Ive attempted to organize all my music in Amarok by scanning my music folder(where all my music is located) first, ive noticed that once it allocates my music to their categories that it is not all there, when i scanned i got a message from Amarok saying that the certain listed files couldnt be scanned and had to be skipped. Why is this? these same songs worked flawlessly in my xp system using winamp. I think i have the right codecs too as i can play mp3 without any problem and i think the same is true for wma. oddly enough, sometimes i can get one of the files that amarok doesnt like to work when i open it manually in Amarok.

Secondly i find the organization of Amarok's collection a bit strange. For example, much of my music(im sorting by artist) is being displayed under a folder called "various Artists" now ive gone and checked the tag info for these songs and each one is labeled correctly and should then go to its artist name right? for example, i have 5 songs by 50cent in their respect alphabetical folder and one in the varius artists folder. they are all tagged with the same artist and yet they are not all in the same place.


thanks for the help! im loving Ubuntu and leaving microsoft, without this community i would have never even considered the move
__________________

---

### Post by haldean on 2007-11-01
Not sure about the first one - I've used Amarok for a while and haven't run into that.

The second one tho - it does that because it's organizing by Album Artist, which is different from the Artist. If you have a bunch of Mix CDs, it'll display them all under "Various Artists". The way I've gotten around it is to use "iPod View" - click the little USB Stick icon above the collection.

---

### Post by skymera on 2007-11-01
most likely not playing becuase of no codec etc blah blah

try this: weorked for meeee

sudo apt-get install libxine1-plugins

---

### Post by Kitsun on 2007-11-01
If you right-click the artists name and select "Do not show under Various Artists" it will show under the artists name.

---

### Post by GeneticFlea on 2007-11-03
thank you soo much! both the ipod method and the right click option worked. thanks for fixing this noob up, ill check to make sure i have all the needed codecs. 

great community!

---

