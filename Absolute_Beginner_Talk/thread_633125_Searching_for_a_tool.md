---
title: "Searching for a tool"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-12-06
im searching for tool that can cut some part from mp3 file and save it
like the avidemux but for mp3 files because avidemux only support movies
i tryed Audacity but it is too hard ... so is there another app that can do this work?
i just need something like start point 00:01:00 and end point 00:02:30 and it will copy this 1:30 minutes to other file.. 
thanks

---

### Post by Dr Small on 2007-12-06
Audacity can do it, but you can not save it as a MP3 unless you get proper codecs for that.
But all you do, is swipe a parts around the piece you want to save, and cut them, until all you have it the piece you wanted, and then you save it.

---

### Post by drs305 on 2007-12-06
I know you said audacity was too hard. I am using Audacity beta 1.3.3. To do what you want:
Open the mp3
My audacity app has a section on the bottom that shows start and stop times. 
Enter start time, enter stop time. This will highlight the selected time.
Edit, Trim. This will eliminate everything else.
File, Export, (select MP3 in lower right corner), enter name at top, Save.
Done.

Audacity is a great tool. It has a lot of features that make it a bit overwhelming for a new user, but it can be simple once you get the hang of it. That being said, I am sure there are simpler apps that will do what you want and hopefully you will find one.

---

### Post by subs on 2007-12-06
the audacity program is perhaps one of the strongest(if not the most) audio editing softwares.... unless u go in for licensed software for which u have to dish out cash....

try this tutorial.... it may help u figure out audacity 

> 

[http://www.linux.com/articles/35886](http://www.linux.com/articles/35886)

[http://www.edhsonline.org/other/audacity/](http://www.edhsonline.org/other/audacity/)      <<--- TRY THIS ONE FIRST

[http://audacity.sourceforge.net/manual-1.2/tutorials.html](http://audacity.sourceforge.net/manual-1.2/tutorials.html)


---

### Post by snake444 on 2007-12-06
ok thanks for your replyes but the only problem i have that in here:
> **drs305 said:**
> 
File, Export, (select MP3 in lower right corner), enter name at top, Save.
Done.


there isnt mp3 option, and i need to export it as mp3 because it is for mobile phone
and wav file size is too much

so how can i make it will export the file as .mp3 ?

---

### Post by drs305 on 2007-12-08
> **snake444 said:**
> ok thanks for your replyes but the only problem i have that in here:
there isnt mp3 option, and i need to export it as mp3 because it is for mobile phone
and wav file size is too much
so how can i make it will export the file as .mp3 ?

Snake444,

Sorry you haven't received a quicker response, I've been away a few days. If you are still interested in Audacity, you have to install and point to some libraries to work with mp3's. In Audacity (1.3.3-beta - the instructions may be a bit different in earlier versions):

Edit, Preferences, File Formats
At the bottom of the page, "Download free copy of LAME" (you may already have this)
Then, on the same page, lower right:
Find library (/usr/lib/libmp3lame.so), Yes when it asks to search for the libmp3lame.so (shared object) file.
Change the file name by adding a dot zero to the end: libmp3lame.so.0
Click OK to the warning and then note that mp3 encoding with 128 bit is now enabled.
Close Audacity Preferences. You should now be able to export recordings as MP3s 

The detailed instructions are about half way down the page (Linux) at:
[http://audacityteam.org/wiki/index.php?title=Lame_Installation](http://audacityteam.org/wiki/index.php?title=Lame_Installation)

Please report back on success or failure with this as there are others who can benefit if we can get the instructions correct. Good luck.

---

### Post by a-converted-sparky on 2008-01-29
drs305, i followed your instructions i can now encode in MP3 - yaye!
Im trying to trim up some of my mp3s BUT when i try to play the file in i cannot hear anything? i can see the volumes etc going up down...

Sound does work on ubuntu .... any ideas?  - 

btw i am still a very fresh newbie, but loving ubuntu

---

### Post by drs305 on 2008-01-30
Glad you have had some success - but I guess if you can't listen to the product an audio program creates there is still work to be done ;)

I'm on vacation so hopefully someone will come to your rescue before I get home.  I think in the preferences the IO was set to ALSA default on my machine. There were a couple of other settings I think I had to tweak as well. I'll check back when I get home.


Edited 2/2/2008:  I've sent you a PM with a couple of suggestions.

---

