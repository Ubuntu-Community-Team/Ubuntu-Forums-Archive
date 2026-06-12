---
title: "Rhythmbox Playlist disappears? mp3s on LaCie (Solved)"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by dyingsun on 2006-10-17
Hi all,
I have all my CD's backed up on a 250gb LaCie. Each CD has its own folder, as does each artist. Under XP I used Real Player with which I could scan the entire drive and it would automatically add any mp3 files to My Library. I finally, somehow,  got all the songs into my Rhythmbox library, but now the playlist just doesn't show up at all, and the library is empty. Is this because of the LaCie drive? If I switch the drive off, does it just reset and empty the playlist? Or am I not using Rhythmbox properly? I really don't want to have to go and enter the contents of every single subfolder individually, is there a way I could enter each mp3 into one huge playlist, perhaps through the CLI with a subdirectory switch? I've tried hard to nut this one out, and I'm getting nowhere.

Thanks!
DS

P.S.  No, I'm not mistaking the Queue for the Playlist (anymore!)

---

### Post by aysiu on 2006-10-17
The library should not reset, but it will try to read it from the same place as last time... if the LaCie drive is off, the songs can't be read.

If you go to Edit > Preferences > Library, you can specify what location Rhythmbox is to scan for music.

You will also see your Rhythmbox database in /home/dyingsun/.gnome2/rhythmbox/rhythmdb.xml

---

### Post by dyingsun on 2006-10-17
Aha, that's done it :)
At some time I must have tried to access it while the drive was turned off...I had the LaCie specified as the place to search for songs, but I hadn't checked the "Watch My Library for new files" checkbox. Soon as I checked that, the drive started thunking and lo! the mp3 list appeared.

Thanks for that aysiu! 

DS

---

