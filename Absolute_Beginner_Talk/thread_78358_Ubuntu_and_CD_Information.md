---
title: "Ubuntu and CD Information"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by kimvall on 2005-10-18
Hey all, I just switched from Windows to Ubuntu and seem to be sticking with Ubuntu this time.

In any case, in my Windows environment , I had information about all my CDs (which artist, tracks, and so forth) stored in the cdplayer.ini file. So my question is; does Ubuntu have any support for something similar? I noticed that when I put a CD into my CD player, most Ubuntu software collects info about the CD online. But as I listed to very odd artists, I really like to rely on my own info about the CD I listen to, rather than what other people have submitted (which is usually inaccurate, or the info isn't there to begin with).

Any pointers? Perhaps there's some thread I can read up on?

Thanks in advance.

---

### Post by davmac on 2005-10-18
I was curious about whether this was possible so did a fair bit of googling about. The news isn't too good... The most promising thing I came up with was a windows shareware app (spit!) called MusiCat which can import and export cdplayer.ini. Doesn't say what it can export it to, but cross your fingers....

You can read more about and download the 30-day crippleware from [http://www.sonicspot.com/musicat/musicat.html](http://www.sonicspot.com/musicat/musicat.html)

Dave MacLeod

---

### Post by kimvall on 2005-10-18
Hey Dave, thanks for the info. However, I think you misunderstod me. I wasn't looking for a way to convert the cdplayer.ini file to Linux format (I've converted the file to mySQL database from which I can substract the track info in whatever format is needed). I'm essentially looking for confirmation that there is some sort of support in Ubuntu for keeping the CD data locally, and not having to rely on the info that's available online.

- Jonas

---

### Post by davmac on 2005-10-18
Ahhhhh (clink) That was the penny dropping!

Looking through my home directory, I notice there is a directory called .cddbslave (note the dot at the front) and in there are a number of files - one for each CD I've ripped I suspect and, opening a file up, it is full of track names and more info about the CD. So the answer to your question is "Yes"!

HTH,

Dave Mac

BTW: If you can't see the folder when you're looking for it, it is because files and directories prefixed by "." are hidden. In nautilus Ctrl-H toggles the viewing of these files.

---

### Post by kimvall on 2005-10-18
That is excellent news. Thanks so much. A solutions is in sight!

However, which program do you use to rip and encode the mp3s? I just ripped and encoded a CD with Sound Juicer, but no .cddbslave in sight (I turned on the "view hidden folders" option, so I can see all the other hidden folders, but not it).

- J

---

### Post by davmac on 2005-10-19
I use Goobox

Dave Mac

---

