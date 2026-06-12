---
title: "how do i change a default app"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by demiurgen on 2007-07-30
i installed azureus just after installing ubuntu.
then i discovered that deluge is much better.

but everytime i click on a torrent link in firefox it starts up azureus.
and when i remove azureus ubuntu tells me that the default app for handling torrent files is missing.

how can i change this so that when i click on a link in firefox it starts up deluge instead of azureus???

---

### Post by Inxsible on 2007-07-30
when you click on the link, firefox will ask you which app to use for that type of file. Select deluge from usr/bin/deluge and you should be good to go.

Another way is to download a .torrent file. Right click on it and then go to Open With Tab and select Deluge.

---

### Post by demiurgen on 2007-07-30
hehe.
well i did that the first time and ticked the box for "never ask this question again". :(

and when i download a torrent file and rightclick it and choose to open in deluge it only works on that file and the next file still opens in azureus.

---

### Post by mcduck on 2007-07-30
> **demiurgen said:**
> hehe.
well i did that the first time and ticked the box for "never ask this question again". :(

and when i download a torrent file and rightclick it and choose to open in deluge it only works on that file and the next file still opens in azureus.

It doesn't work if you just right-click and select "Open With". You have to right-click, select "Properties" and *then* "Open With" :)

---

### Post by asmoore82 on 2007-07-30
Firefox has begun maintaining its own set of "default application" rules ...

open firefox and 'Edit->Preferences->Content->Filetypes->Manage' and see if torrents are in there.

---

