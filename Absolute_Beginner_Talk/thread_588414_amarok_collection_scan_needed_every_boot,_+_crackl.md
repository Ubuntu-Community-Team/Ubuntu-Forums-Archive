---
title: "amarok collection scan needed every boot, + crackling crossfade"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by albesan on 2007-10-23
hello team,

Amarok keeps forgetting where the music files are, even though it is properly set on amarok preferences, and the disk seems to always mount at the same point.

Anybody seen this on before?

Also, the sound crackles quite bad on some crossfades.

any comments welcome, thanks.

a.

---

### Post by Vansinnesvisan on 2007-10-23
Which database (SQLite/mySQL) was Amarok configured with? Are they installed with their dependencies? 

Is your music collection on a different hard drive? Perhaps an NTFS one?

Sound crackling could be do to the PCM setting under you sound control panel being turned up high.

---

### Post by Vansinnesvisan on 2007-10-23
> **albesan said:**
> and the disk seems to always mount at the same point.


If you do have the collection on a different drive, this might be helpful:

> The other option is when you configure the collection. Setting -> Configure Amarok and then click on the "Collection" option. This is where you set what directories to find your music files. Here you will see a checkbox for "Watch folders for changes". Uncheck this, click "OK" and "Rescan Collection" under the tools menu. Then it won't erase the database when it goes to look for the files and the USB disk isn't on as it won't be watching for changes anymore. This just means that as you add new files or make changes, you will have to manually rescan.

[Source]("http://ask.metafilter.com/50710/Help-using-Amarok-with-a-removable-drive")

---

### Post by albesan on 2007-10-24
hey,

thanks for the advice.
I'm using SQlite.
PCM is below 50% I took down a bit further but there is still crakling, although not all of the tunes. Might it be down to volume of individual files?


and yes, I had read that post and my settings for "watch folders for changes" are how you suggest on your post.

having said all of this, today is the first time it doesn't forget where the files live.

thanks again.

a.

---

