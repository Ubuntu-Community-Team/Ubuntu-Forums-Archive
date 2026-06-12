---
title: "Can't change songs' information on Rhythmbox"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-12-03
I can't change the some songs' information on Rhythmbox. Whenever I type the new information on the songs, the new information will applied for seconds and then it change back to old information. I tried EasyTag and then reimport the songs, but the songs still contain the old information.

---

### Post by dbd on 2006-12-04
Could the music files be write protected? To find out go into a directory where one of these songs is and then try and change the filename (using your normal user, not root). If you can't change the filename then the song is write protected, to fix this it could be useful to know how far the write protection spreads. Is it the whole partition or just a few of the files on that partition that you can't change?

If it is a whole partition then it could be useful to see /etc/fstab to help fixing it.

---

### Post by oliviacond on 2006-12-04
weird. The songs in the directory contains new information. But they contain old information in Rhythmbox. 
old information=the songs name is in Japanese
new information=the songs name is in English

---

### Post by dbd on 2006-12-05
Hmm, that is strange. I don't know Rhythmbox, but is there a way you can remove the files and then add them again? Reloading them may help.

---

### Post by bom28 on 2006-12-05
It's probably because there is APE tags in addition to id3v1/2 tags in your mp3 files.
I know Gmusicbrowser can edit/remove them, though if you want to remove them you have to go in the advanced tag editing in the song properties dialog for each file one at the time.

A quick google search turned up that link : [http://forums.slimdevices.com/showthread.php?t=29577]("http://forums.slimdevices.com/showthread.php?t=29577")
it seems easytag can remove APE tags in mp3 files if you rename the .mp3 file in .mpc.

---

### Post by oliviacond on 2006-12-07
problem solved. thank you. :)

---

