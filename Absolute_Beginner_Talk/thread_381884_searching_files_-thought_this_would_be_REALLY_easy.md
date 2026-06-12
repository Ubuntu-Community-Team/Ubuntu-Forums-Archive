---
title: "searching files -thought this would be REALLY easy..."
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Lor Boo on 2007-03-11
K - thought this would be dirt easy but yet...here I post...

[COLOR="DarkRed"]**_Situation._**[/COLOR]
I have a friends hdb runing Winxp on fat32 mounted to /mnt/tom 
I'm running 6.10 with hda and sda being my standard hard drives.  
(at least I think i'm running 6.10 - how does one check?)

[COLOR="DarkRed"]**_Issue:_**[/COLOR]
I want a gui seach tool to find *.mp3's off this disk to burn to DVD before wiping his system.
I could just browse for them, but it would be tedius and I wouldn't really learn anything either.

[COLOR="DarkRed"]**_What have I tried?_**[/COLOR]
Tried the gui -> Places -> search 
but it appears to only search my desktop?

Hit Preferences and added /mnt/tom and then searched for:  *.mp3  and then .mp3
No results were returned from his harddrive.  I'm not certain if the search is checked subdirectories?

I installed Beagle a while back - but don't see how to use it
I tried the live CD (ver 5.04) and it's "places - search" found all his MP3's...
but searching from my updated system is failing.

I've checked around the rest of the menu's but see nothing else to use.

Also I've tried the 'find' command.  It didn't work so good for me...however I realized i'd prefer to use the GUI in this case anyway as I 
want to burn off mp3's from multiple directorys to DVD and CTRL-A and the mouse don't work so good in the terminal...


Back reading on this didn't turn this up either as everything I found was either completely not related, or... just not really related..... ](*,) 

[COLOR="Navy"]**How can I search the file system for *.mp3?**[/COLOR]

---

### Post by tribble222 on 2007-03-11
Places --> search should work.  Did you change the "look in folder" drop-down to /mnt/tom?

---

### Post by Najand on 2007-03-11
Use command:
```

find /mnt/tom -iname *mp3

```
in the terminal.

---

### Post by Lor Boo on 2007-03-11
Tribble - I do not see a 'look in' option any place.

What I have in the search windows are - 
(- btw help informs me is Beagle Search 0.2.6 -)

Search - Sort - Help

Under Search I have different kinds of media.
but nothing related to different places to search unless I go under 'Preference'
In there I can add /mnt/tom
I would hope it would search sub-directories ... prehapes this is the place i'm going off the tracks?

I've found this site:
[http://nat.org/demos/](http://nat.org/demos/)

I'm looking at the video's now... but will keep this thread open as well.
Thanks

---

### Post by DarkN00b on 2007-03-11
This is why I use the "Search for Files" panel applet (Gnome). It is much more intuitive and easy to use.

---

### Post by tribble222 on 2007-03-11
Strange.  Well you can always just use the command line.  I realize Najand's command won't really help you because you actually want to be able to drag the files to burn them.  But how about this

find /mnt/tom -iname *mp3  -exec cp {} /mnt/tom/allmp3sgohere \;

That will find all mp3's and move them to the directory /mnt/tom/allmp3sgohere

Or you could change mv to cp if you want to retain the original files.  Make sure whatever directory you're moving them to exists before you initiate the move.

---

### Post by Najand on 2007-03-11
> **tribble222 said:**
> Strange.  Well you can always just use the command line.  I realize Najand's command won't really help you because you actually want to be able to drag the files to burn them.  But how about this

find /mnt/tom -iname *mp3  -exec cp {} /mnt/tom/allmp3sgohere \;

That will find all mp3's and move them to the directory /mnt/tom/allmp3sgohere

Or you could change mv to cp if you want to retain the original files.  Make sure whatever directory you're moving them to exists before you initiate the move.

Well, I just tried to help him/her to find his/her files. I am sorry if I helped in a wrong way.

---

### Post by tribble222 on 2007-03-11
> **Najand said:**
> Well, I just tried to help him/her to find his/her files. I am sorry if I helped in a wrong way.

No, all helping is good, no offense was intended!  My intent in mentioning your post was actually to respect your help rather than just "countermanding" it with a command of my own.

---

### Post by Lor Boo on 2007-03-11
Thank you much all.
Adding in the applet did the trick... searched the folder and the subfolders...
files in a bunch of places (3 users of the computer) now all going to 2 DVD.


Thanks for the command line.
it's good to know that one.
I just didn't want to have to move the files one folder at a time.... too much time.
Is good here now.


One another note - I really have noticed a strong climb in support with ubuntu as well - 
from the days of red hat 9, mandrake... 

thanks all.

---

