---
title: "Trying to access files on a mac hdd"
date: 2009-01-12
forum: Apple Hardware Users
---

### Post by djkhl930 on 2009-01-12
hey im new to ubuntu, and ive been trying access these files on an old mac hdd. I can see the hdd and all the folders in it, i just cant access some folders, specifically my user folders, with all my music, photos,etc. They have an x next to them and they say that i dont have sufficient privileges to access them. I was wondering what i needed to do to override this so that i can get access to my music.
(PS: I cant put the hdd into my mac seeing as its dead now)

---

### Post by bryonak on 2009-01-12
[Here]("http://ubuntuforums.org/showthread.php?t=1031842") you go.

You could also change the permissions by fiddling with the mount and user id options (it's not that hard, but quite technical).

Also note that in order to write to your HFS+ partition, you have to disable it's journaling with the diskutil in a suitable OSX (if you can attach your HD to one). Otherwise your best bet is to backup everything and format it to ext3.

---

