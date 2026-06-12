---
title: "Music and Videos"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by at0mik on 2007-03-24
Was wondering if someone could help, I'm trying to play mp3/wma files, tried to play in Rhythmbox Music Player and installed amaroK and juK but none of them work properly. I can see the files listed in the playlists (of amaroK and juK) but it doesn't play it onto my speakers :confused:.

Also, MPlayer doesn't play any DVD's or movies files (.mp4, etc). I tried looking in the online documentation in the RestrictedFormats but it doesn't give a clue as to what I should do. I'm a complete noob at this, lol :P.

---

### Post by dptxp on 2007-03-24
Have you installed audio video coces using Add/remove ? They are listed as community software under audio/video after you click add/remove.

---

### Post by at0mik on 2007-03-24
> **dptxp said:**
> Have you installed audio video coces using Add/remove ? They are listed as community software under audio/video after you click add/remove.
Theres no community software option in "Sound & Video".

---

### Post by at0mik on 2007-03-25
Anyone?

---

### Post by dptxp on 2007-03-25
It is not listed as community software. Chooser Audio/Video,Scroll down the programs on right, you will see mp3 codecs, and video codecs next. The description below will tell you that these are community software, i.e., maintained by community.

---

### Post by at0mik on 2007-03-25
There are no codec files that I could see :confused:. Just to be sure, I installed everything that was in "Sound & Video" which can be seen in the picture but still no audio (theres nothing wrong with my hardware because I can hear the sounds when Ubuntu starts up including the drums and nature :P).

[IMG]http://img339.imageshack.us/img339/1920/screenshotfh8.png[/IMG]

---

### Post by ramzai on 2007-03-25
The easiest way is

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_386.29)

---

### Post by dptxp on 2007-03-25
scroll down, scroll down the right side where the list is. It is almost at end.
You are at right place. You will see mp3 in description on
right.
you do not need automatix for this.
I shall check on my laptop and le you know in a few hours.

---

### Post by at0mik on 2007-03-25
There is only "Volume Monitor", "Xfmedia" and "XMMS Music Player".

[img]http://img231.imageshack.us/img231/6750/screenshot1vt2.png[/img]

---

### Post by halitech on 2007-03-25
do you have the actual codecs installed? Ubuntu does not ship with them by default so if you don;t have them installed, you won't be playing them. go into Synaptic 

System - Administration - Synaptic Package manager

then go to Settings - Repositories and enable Multiverse and universe.

then reload and you should be able to find and install the codecs.

---

### Post by at0mik on 2007-03-25
> **halitech said:**
> do you have the actual codecs installed? Ubuntu does not ship with them by default so if you don;t have them installed, you won't be playing them. go into Synaptic 

System - Administration - Synaptic Package manager

then go to Settings - Repositories and enable Multiverse and universe.

then reload and you should be able to find and install the codecs.
Alright I found the codecs, would you be able to tell me which ones to install?

---

### Post by jackrobinson on 2007-03-25
add-remove is a bloated mess. use automatix.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by halitech on 2007-03-25
the main one you want is w32codecs, it will give you most of what you need. 

and yes, automatix is good but, with the server issues they've been having lately, might as well do it the manual way so it gets done without waiting.

---

### Post by jackrobinson on 2007-03-26
> **halitech said:**
> the main one you want is w32codecs, it will give you most of what you need. 

and yes, automatix is good but, with the server issues they've been having lately, might as well do it the manual way so it gets done without waiting.

They are now on a dedicated server. Seems like their outages are a thing of the past.

---

### Post by dptxp on 2007-03-26
Sorry for late reply.

The items to be ticked are (in Sound and Video)
1)Gstreamer extra plugins
2)GsTreamer ffmpeg video plugin.
Next click OK.

Do not un-tick any other.

I have 64 bit, but 32 bit should have these.

Personally, I keep off fro automatix, though I have 64 bit.

---

### Post by at0mik on 2007-03-28
Thanks everyone for your help (especially dptxp and hailtech :)). Now Ubuntu is that much better :D :p.

---

