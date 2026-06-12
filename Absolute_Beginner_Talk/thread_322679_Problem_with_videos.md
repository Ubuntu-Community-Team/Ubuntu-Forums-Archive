---
title: "Problem with videos"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by JesusAddict3791 on 2006-12-20
I can't get any videos to play on my new Edgy install on my laptop. I've tried different formats (mpg, divx, wmv) on different players (totem and mplayer) and all I get are error messages. 

Mplayer always says "Error opening/initializing the selected video_out (-vo) device." 

Totem always says "You do not have a decoder installed to handle this file. You might need to install the necessary plugins."

The messages are the same for all video types except for when I try to play a DVD in Totem. Then it says "No URI handler implemented for "dvd"." Mplayer gives its normal message for DVDs.

My first thought is that it's a driver issue, but I have no idea what to do about it. What do you guys think?

---

### Post by loserboy on 2006-12-20
I dunno much about these things, but have u installed all the codecs?

---

### Post by r4ik on 2006-12-20
This might help,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Good luck !

---

### Post by JesusAddict3791 on 2006-12-20
I had tried installing the gstreamer codecs, which didn't work. But the reason it didn't work may have been because they didn't install for some reason. Update Manager listed them as not installed, so I installed them. Now Totem is playing movies, but at like 4x speed. Mplayer is still giving the same message.

---

### Post by r4ik on 2006-12-20
Could you try set the Mplayer video output to X11 ?

---

### Post by JesusAddict3791 on 2006-12-20
I don't see where I would set the video output in mplayer, but now it's not giving that error message anymore. It's playing one mpg and DVDs fine now, but for any other video (including other mpgs) it shuts down as soon as it opens the file.

---

### Post by r4ik on 2006-12-20
When it loads the mpeg you should be able to right click and configure.

---

### Post by JesusAddict3791 on 2006-12-20
Ok... I found it. It's already set to X11. When I found it, I had a sudden urge to reboot the machine. After rebooting, Totem is working just fine now except for DVDs. Mplayer is still only working for DVDs and that one mpg. Weird.

---

### Post by r4ik on 2006-12-20
Try to remove Totem using synaptic reason is i am getting the feeling they are in each others way.

---

### Post by loserboy on 2006-12-21
Everytime I do a new install the 1st thing i do is go to [www.getautomatix.com](www.getautomatix.com)
it makes life so much easier as far as codecs, video player, fonts, video drivers, etc.

---

