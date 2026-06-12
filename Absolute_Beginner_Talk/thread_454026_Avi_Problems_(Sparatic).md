---
title: "Avi Problems (Sparatic)"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Dougie187 on 2007-05-25
So i have an odd problem. I have tried using Movie Player, Mplayer, and VLC to play various movies, (Mainly AVI movies, the Starcraft 2 trailers for instance) and a lot of them play. But some of them dont play, what happens is VLC and Movie Player both open and look like they are going to play, and then they close right away. Mplayer gives an error that it cant initialize the output device. I found some threads that covered this topic by changing the video output codec that mplayer uses but that didnt work for me. Anyways, and help would be greatly apperciated.

EDIT: For reference, the Starcraft 2 trailer that wouldnt play for me is the 20 minute gameplay movie. Just so you can download it and try it yourself if you want.

---

### Post by Pragmatist on 2007-05-25
Please post the exact error message.  Also, if you run the movie players from the command line, you should see the errors even after the windows close.

---

### Post by dannyboy79 on 2007-05-25
you should also find out the avi info for the files that DO play versus the avi info for the files that DON'T play. There is a tool called mediainfo, haven't used it yet but other ubuntu's users have. here the link to the source files ([http://mediainfo.sourceforge.net/en/Download](http://mediainfo.sourceforge.net/en/Download)) and heres the link to the thread regarding it's use. ([http://ubuntuforums.org/showthread.php?t=453125](http://ubuntuforums.org/showthread.php?t=453125))

---

### Post by Dougie187 on 2007-05-25
So when I run the video in the command line (that doesnt work) with mplayer, it says the following:

X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0

VLC give the following error:

X Error of failed request: BadAlloc (Insufficient resources for operation)
   Major opcode of failed request: 141 (Xvideo)
   Minor opcode of failed request: 19 ()
   Serial number of failed request: 81
   Current serial number in output stream: 82

Totem (Movie Player) gives the same type of message, that there are insufficient resrources for the operation. 

Any Idea how to give it more resources? Thanks for the tip. I never thought to run the videos in the command line to get errors. I guess it makes sense that this would fail in compairison to the other two, as the other two are only like 5 minute videos, where as this one is 20 minutes.

---

### Post by Pragmatist on 2007-05-25
You could try this person's solution:
[http://www-zeuthen.desy.de/~alorca/linuxonlaptop.html]("http://www-zeuthen.desy.de/%7Ealorca/linuxonlaptop.html")

In a terminal type:
```
mplayer -vo x11 [-ao arts] filename.avi
```

Edit: The URL contains lots of info, to find the part relevant to you, do a find (CTRL F) and use the keyword "badalloc"

---

### Post by Dougie187 on 2007-05-25
Is there maybe a more permanent fix? Or one for VLC or Totem instead of just Mplayer?

---

### Post by Pragmatist on 2007-05-25
> **Dougie187 said:**
> Is there maybe a more permanent fix?...

So the above command worked for you?

---

### Post by Dougie187 on 2007-05-25
Yeah. Except the video is bigger then my monitor resoultion. So I cant see like.. 1/4 of it.

---

### Post by disturbedite on 2007-05-25
i thought i'd just thow this info out in case it helps anyone.

just some facts about the video drivers & players.

the xvideo (xv) driver can't play hi def videos.  i can't remember why.
try using the xshm (called x11/x shim) driver.
you might also try the xine player or a player that utilizes xine like xine-ui or kaffeine.

---

### Post by Pragmatist on 2007-05-25
X11 can apparently be problematic.  Try this invocation:

```
mplayer -vm filename.avi
```

---

### Post by Dougie187 on 2007-05-26
When i called the video using:
mplayer -vm filename.avi
it totally killed my machine. the screen went completely black and I couldn't do anything. Had to hard reboot.

I will give the xine and xshm a try. I'll let you know what i find.

---

### Post by Dougie187 on 2007-05-26
When i tried setting mplayer to use the x11 shm driver (its called x11 in mplayer) It worked the same as when invoked using:
mplayer -vo x11 filename.avi

I couldn't see all of the video the rightmost quarter of the screen was cut off. Then when I installed xine-ui and tried using xine to play the avi file it just closed right away, similar to how the video players acted before using the -vo x11 flag for mplayer.

---

### Post by Dougie187 on 2007-05-26
Alright. So i found a fix. I don't remember the site, but i think it might have been bugs.launchpad. somethingelse.
Anyways.. I guess the main problem is because the video resolution is bigger then my computers resolution, and the xserver doesnt like this very much. So it throws the BadAlloc error. So to remedy this problem I had to add the following line to my xorg.conf Under the Section "Device" area. I also guess this is only "Suposed" to work for intel graphics cards.

The line I had to add was:
    Option   "LinearAlloc"    "8160"

Hope that helps other people with this similar issue.

---

