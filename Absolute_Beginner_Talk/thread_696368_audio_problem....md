---
title: "audio problem..."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-13
with amarok and movie player very often when i play some files or folders it gives me the following message: 
this is on daemon log:
```
...
Feb 14 03:29:35 select-laptop last message repeated 12 times
Feb 14 03:30:35 select-laptop last message repeated 12 times
Feb 14 03:30:37 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:40 select-laptop last message repeated 54501 times
Feb 14 03:30:40 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:30:40 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:45 select-laptop last message repeated 114150 times
Feb 14 03:30:45 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:30:45 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:47 select-laptop last message repeated 9146 times
Feb 14 03:30:50 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:31:25 select-laptop last message repeated 7 times
Feb 14 03:32:30 select-laptop last message repeated 13 times
Feb 14 03:33:35 select-laptop last message repeated 13 times
Feb 14 03:34:35 select-laptop last message repeated 12 times
Feb 14 03:35:35 select-laptop last message repeated 12 times
Feb 14 03:36:35 select-laptop last message repeated 12 times
Feb 14 03:37:35 select-laptop last message repeated 12 times
Feb 14 03:38:35 select-laptop last message repeated 12 times
Feb 14 03:39:35 select-laptop last message repeated 12 times
Feb 14 03:40:35 select-laptop last message repeated 12 times
Feb 14 03:41:35 select-laptop last message repeated 12 times
Feb 14 03:42:35 select-laptop last message repeated 12 times
Feb 14 03:43:05 select-laptop last message repeated 6 times
Feb 14 03:43:08 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:43:10 select-laptop last message repeated 42275 times
Feb 14 03:43:10 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:43:10 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:43:13 select-laptop last message repeated 19795 times
Feb 14 03:43:15 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:43:50 select-laptop last message repeated 7 times
Feb 14 03:44:55 select-laptop last message repeated 13 times
... 
```

on amarok: ```
audio output not availiable
xine paremetres
```
on movie player(xine backend) :```
 The audio device is busy. Is another application using it?
```

any ideas?

---

### Post by natirips on 2008-02-14
Does your audio work at all?
What hardware are you using?

I know I couldn't hear a wisper from my laptop until I installed linux-backports-modules-generic in Synaptic.

---

### Post by dca on 2008-02-14
Too many open files is kind of non-descript...  If I torrent a d/l for a Linux distro (because I never torrent anything illegal) I make sure nothing else is running...  On the amaroK side (not being too familiar application, but) are the same codecs being used between the movie and the music?

---

### Post by someoneouthere on 2008-02-14
> Too many open files is kind of non-descript...  If I torrent a d/l for a Linux distro (because I never torrent anything illegal) I make sure nothing else is running...  On the amaroK side (not being too familiar application, but) are the same codecs being used between the movie and the music?



so this refers only to torrents...?
```
Feb 14 03:30:45 select-laptop avahi-daemon[5731]: accept(): Too many open files
```

as for the codecs i dont know(i think it is)  is there a way to check it out?

---

### Post by natirips on 2008-02-16
I've been thinking about your problem, try using VLC player for all your media if it doesn't represent some inconvenience to you... I've found it being much better than Amarock  or Movie player. If you need playlist I think it is CTRL + P by default. It can save/load playlists normally, supports multistreams etc. etc. Notice however, that VLC 1.0 isn't released yet, it's still an incomplete project. But that is acctually a good thing, it means it will get even better :).

As for avahi-daemon saying too many open files, it has something to do with networking, not audio...

---

