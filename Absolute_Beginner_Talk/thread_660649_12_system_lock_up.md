---
title: "1/2 system lock up???"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-01-07
ok this happened 2 time on me, downloading music via gtk-gnutella and then playing the songs threw media players (forgot what program was playing the songs) so as the music plays i still down load more music but them after one song is finished i try to bouble click another song to play but nothing happens,also under places-homefolder program will not open same for the rest of the folder under places, can open firefox  and post her but nothing else, last time this happened had to restart computer,
:confused::confused::confused:
help:lolflag:

---

### Post by broekskw on 2008-01-07
ok looks like i can use all icons under system and applications just not under places, nothing happens when i select an icon under places, also all my icons on my desktop are missing?? and yes i know about the right bottom corner icon for switching from one screen to another but both are missing all my icons?:confused:

any suggestions

---

### Post by broekskw on 2008-01-07
so it did it again most of my desktop icons are gone and can not access under places>home folder
places>desktop
places>documents,music,pictures, or video

is there a command in terminal that will unlock anything that is locked up??

please help hate doing a reboot all the time:confused:

---

### Post by jtravnick on 2008-03-05
Have you found out what was doing this yet? I to am having a problem like what you describe. 

What will happen is while I'm downloading I listen to a song that I downloaded to make sure it is really what I want before moving it out of /gtk-gnutella-downloads/complete to the folder that I want it in.
All of a sudden I can no longer click on a file and none of the things in Places can be opened. Also I can not use System Quit but the button over by my clock will let me shut down.

Is our only alternative to install a different file share??

Jim

---

### Post by cbiere on 2008-03-05
Your problem isn't gtk-gnutella. Most-likely the player is causing this.  You don't have to reboot. Just switch to a virtual console, login and kill whatever player is running like this:

pkill -9 mplayer xine vlc amarok

That should release your "desktop".

---

