---
title: "Beagle search questions"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-06-29
I have been investigating the usefulness of various desktop search utilities.  I have tried affinity with little success, tracker with even less success and finally settled on Beagle which seems to be the only one I can get to work at all.  Tracker does not find anything? I cannot seem to get affinity linking with either Beagle or Tracker.
My questions are about Beagle:
It does not seem to find separate files contained within folders, ie it will find the folder for the artist but no tracks within that folder.
It will also not find any open office files (.odt), I know the files are there and Beagle has finished indexing, if a search is done with the deskbar it finds the files OK.

There does not seem much point in Beagle using the resources when it will not find what is clearly there.

Any ideas or reasons anyone could think of for this before I uninstall.

I am really tempted to try out Google desktop for linux but it looks a bit scary  (privacy issues,  can I get rid of it if I do not like it?

---

### Post by hanzomon4 on 2007-06-29
Just let beagle finish indexing and all should be well, however beagle indexing is retarded and sometimes it just seems to hang. You can check to see what all has been indexed by putting beagle-index-info in a terminal. Once all of you data has been indexed it will work great, the actual indexing is the trick with both beagle and tracker. Try Google Desktop it's dead simple to use, faster, and less of a resource hog. It can't index everything beagle can but it works for the basics.

---

### Post by Campingman on 2007-06-29
Thanks hanzomon,
I will leave it overnight, it seems a bit odd that it has found all the folders containing the tracks but not the data inside the folders.  It does not recognise any odt files, a search for any of them comes up blank.  They are contained in a slave fat drive.  
It is a bit of a resource hog I must admit.
If I try google desktop via their deb package how do I remove it?

---

### Post by hanzomon4 on 2007-06-29
Yeah I had the same issue with beagle only finding the artist folder, for example, and not the actual mp3s tagged with that artist. Letting it index for a day or so fixed it. You can test things like your music files by searching this query **artist:Artist name**, this should look for all music files tagged with the artist's name. The query **artist:Sonic Youth** would find all of my sonic youth music files. You can do the same with extensions, **ext:odt  hanzomon4**(Thats ext : odt) this would find any odt with hanzomon4 in it. I would run little searches like that for things that I know should be in beagle's index path and just keep waiting until the show up.
  
Remove Google  Desktop in this way:```
sudo apt-get remove google-desktop-linux
```

---

