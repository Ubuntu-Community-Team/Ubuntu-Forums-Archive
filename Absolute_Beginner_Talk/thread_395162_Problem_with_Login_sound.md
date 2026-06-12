---
title: "Problem with Login sound"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by wscheer on 2007-03-27
Made a bit of a goof here #-o 

I went into System > Preferences > Sounds and changed my login to a WAV file that Ubuntu does not like. Now when I try to login, Ubuntu hangs at the point right before it would usually play the song.

I log into the terminal, is there any way to change the login sound through the terminal? I don't know if there is a conf file or if I can just delete the file. I did a "locate" on the name of the WAV file, but the only one that it found was the one on my Desktop. I was unable to delete it because Ubuntu says file not found.

any help would be much appreciated.

* I installed "/" on its own partition, if worse comes to worse I can always reinstall *

---

### Post by useResa on 2007-03-28
Assuming you are using GNOME, you can do so by editing the gmd.conf file which is located in the /etc/X11/gdm directory.

Scroll down the file (quite some pages) and you will encounter the line
> SoundOnLogin=true
You can alter this to false.

Just below this line there is another line which indicates
> SoundOnLoginFile=<name of file>
Guess this where you will find the wav file you indicated as being the one to sound.
In my case the name of the file indicated is: /usr/share/sounds/question.wav
I guess another option is to put in the name of this file.

I hope this will help to solve your problem.

---

### Post by wscheer on 2007-03-28
OH THANK YOU USERESA!

I can't wait to get home and try that. I knew there had to be some way around it. I'll repost after I try it. You just made my day!

*note to self: when experimenting with sounds, change the LOGOUT sound first :roll: *

---

### Post by wscheer on 2007-03-28
useResa,
Bad news, I edited the gdm.conf file and tried all sorts of combinations of setting all sounds to false, all sounds to true, ect..., but none of them seemed to work.

It did change the sounds when I initially got to the login screen but after I put in my name and password and hit enter, it still hung on me.

I'm going to reinstall since I made a separate partition for "/" but I wanted to thank you for taking some time to answer my question.

---

### Post by wscheer on 2007-03-29
Just an update, I reinstalled and everything seems to be working great now.

---

### Post by useResa on 2007-03-29
> **wscheer said:**
> Just an update, I reinstalled and everything seems to be working great now.
Glad that you have everything up and running again.
Sorry that my suggestions did not help you.

---

