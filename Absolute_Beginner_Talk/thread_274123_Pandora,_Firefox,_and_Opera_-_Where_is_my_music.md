---
title: "Pandora, Firefox, and Opera - Where is my music?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by CupofDice on 2006-10-09
Just wondering where does Opera and Firefox store music from pandora. I looked in home/.opera, but it doesn't seem to be there.


Also, and this isn't that important, but I just starting using opera's pandora widget, and it automatically logged me into pandora. I have no passwords stored with Opera, and KeePassX is closed (I did have it opened earlier, but I restarted). Just something a bit weird.:-k

---

### Post by smartalecks on 2006-10-09
I'm pretty sure that pandora streams the music, and firefox and opera don't keep the music. It's like when you are listening to internet radio- you don't get to keep the music (although it is possible).

---

### Post by bswilson on 2006-10-09
Um, I don't think that music you listen to from Pandora is stored on your computer.  You're listening to a stream of music.  If Pandora saved the music on your computer, that would be **illegal**.

---

### Post by CupofDice on 2006-10-09
It stored music on Windows. All you had to do (if using Firefox) was run %temp%, and tag on .mp3 to the file. I know there was a method for opera too (more complicated).

Just found some info here on audacity.
[http://www.mp3car.com/vbulletin/showthread.php?t=66247]("http://www.mp3car.com/vbulletin/showthread.php?t=66247")

---

### Post by tlacuache on 2007-02-13
Don't know if this thread is dead, but I found that in firefox the pandora songs were actually stored in the memory cache. I could actually "download" them (ie., save them to disc) by entering

```
about:cache?device=memory
```

in the location bar, and finding the large files from Pandora.

Admittedly, this is more of a pain than the way you mentioned doing it in windows. Since I've got 2GB of RAM to kill, I actually ended up running a firefox browser in wine and grabbing the pandora files out of ~/.wine/drive_c/windows/temp when I wanted a copy of a song. :)

---

