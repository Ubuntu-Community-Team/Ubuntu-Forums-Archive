---
title: "No Video visible"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Pod_Man on 2005-12-16
Im trying to watch a movie in totem. I installed all the proper stuff for dvd playback, and i get sound, and the aspect ratio changes as the video changes from fullscreen previews to wide screen, but i cant see any thing! just a blank screen. Any suggestions? And i would like to enable the 5.1 surround as well on my soundblaster live. any suggestions for this?

---

### Post by Mustard on 2005-12-16
Hmmm..havent seen that problem before.  It might be something that others have gone through though.  Have you tried the search function in the forum or googled up with some keywords that might allow you to find others who have online records of this problem (and hopefully their solutions)?

---

### Post by Mustard on 2005-12-16
Have you tried installing totem-xine instead of totem?

To double check your setup it might be helpful (or not), to go over this guide and confirm you have done each step too.

[http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)

---

### Post by Mustard on 2005-12-16
With regards to the surround sound, try installing alsamixer using synaptic ( I think  have the spelling of the package correct).  It runs in terminal as a very basic terminal 'gui'.

---

### Post by Pod_Man on 2005-12-16
in regards to the video, i have followed that tutorial, and it didnt work. and i also have run the alsamixer and adjusted my volumes, and im still not getting 5.1 out of my speakers. this is kind of frustrating, because google is not really producing any results

---

### Post by Mustard on 2005-12-16
As another angle  to try with the surround sound problem.  Have you gone to the master volume control icon in the top right corner of your gnome desktop and double clicked...gone to preferences and added any volume controls that might have some relevance to surround sound.

Also have you double checked that you have adjusted any actual volume controls on your speakers, physically?

Just from a conversation I had in the IRC channel many moons ago, I recall there being some strange occurences with the volume setting and surround sound.  Sometimes a set of speakers where being controlled by a volume control that seemed the opposite of what it should have been.

Sound problems are quite often a pain to troubleshoot, so I don't envy your situation.

---

### Post by Pod_Man on 2005-12-17
okay...this is strange. i have been using a single monitor, but have two hooked up. (i just havent figured out monitor spanning yet) i turned the other one on...and it plays video just fine! they are mirroring each other, one has the black screen and the other plays the video. weird...the video is choppy though...any tips? and any answers on the 5.1 issue yet? i made sure that totems output was 5.1 and nothing yet

---

### Post by Mustard on 2005-12-17
The choppy video may be due to dma not being enabled. Try this wiki guide to enable dma.

Read the warning at the top of the page first.  Especially if your machine is older than 3 years.

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

On the surround sound front, I have only found these two threads so far...

[http://www.ubuntuforums.org/showthread.php?t=88655&highlight=enable+5.1+surround+sound](http://www.ubuntuforums.org/showthread.php?t=88655&highlight=enable+5.1+surround+sound)
[http://www.ubuntuforums.org/showthread.php?t=69027&highlight=enable+5.1+surround+sound](http://www.ubuntuforums.org/showthread.php?t=69027&highlight=enable+5.1+surround+sound)

---

### Post by Pod_Man on 2005-12-18
okay...so heres the deal(s) now. i had to reinstall ubuntu because of something weird that came up, and now some things arent working. i enabled DMA and i now cant play dvds. i naturally assumed this was because of the dma, so i downloaded an mpeg file to play, went to the how to and got the codecs and followed the instructions there, and totem says it cant play that stream, try downloading the appropriate codecs. im stumped here guys. right now in my mind, windows trounces linux in the arena of multimedia. this has been quite a pain to get set up properly...

::EDIT:: alright, now its official. i undid the changes to my drive config file and got rid of DMA, rebooted, checked to make sure it was off, and dvd still wont play. whats going on and why is it so hard to do multimedia stuff with ubuntu? its really frustrating...i just want to be able to watch a movie...

---

### Post by Pod_Man on 2005-12-18
::Bump:: Still cant watch dvds or any movies for that matter, any suggestions? other apps perhaps?

---

