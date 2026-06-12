---
title: "Photo Frame"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by easment on 2006-08-17
Hey, I'm jumping on the digital photo from from old laptop. One of the guys I work with says he has heard good things about Ubuntu so I gave it a go. It installed quite painlessly and was quite impressed. I tried an old mandrake linux install 4 years ago and never got it working.

I have a couple questions since I am a linux newbie and tried searching a round, but never found an answer. Here goes:

I discovered gthumb's slide show and it is just what I am looking for. Is there a way that I can make this program run in slideshow mode on startup. Possible issues: a) write a script to login with my usename and pass. b) a script to startup gthumb in slideshow mode

Could someone point me in the right direction? I may be biting off more than i can chew, but it seems that getting it to autologin shouldn't be too bad. however, getting gthumb to startup in slideshow seems that it may be impossible. Thoughts?

---

### Post by taurus on 2006-08-17
In gThumb, look in Edit -> Preferences for your slideshow config!  And if you want gThumb to start when you log in, then just add it to your session, System -> Preferences -> Sessions -> Startup Programs and click Add.  Then add gthumb to it and save it...

---

### Post by meng on 2006-08-17
It's possible:
1) System > Admin > Login Window > Security > Enable automatic login
2) System > Preferences > Sessions > Startup Programs
You create an entry "gthumb ..."
The ... is for the extra arguments/parameters to pass, i.e. starting directory and slideshow mode. But you'll have to type "gthumb --help" in a terminal to figure out the required arguments, I don't know them offhand.

---

### Post by jaybmx on 2006-08-17
wow, great thread!:p

---

