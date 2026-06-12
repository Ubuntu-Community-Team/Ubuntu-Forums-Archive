---
title: "gthumb - imports only old and deleted photos"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by tswanee on 2007-07-04
When I try to import photos, only a few old and allready deleted photos are showing. This is a problem with both my digitals cameras. I guess there is a log file I can delete somewhere, but I don't know where to find it...

I am using 6.06.

---

### Post by alienexplorers on 2007-07-04
Your thumbnails are stored in the .thumbnails directory.  cleaning that will cause new pictures to be displayed.  I use a small script file to keep .thumbnails clean.
> #!/bin/sh
echo "starting cleanup"
sleep 2
echo
echo "deleting large thumbs"
sleep 2
cd /
cd /home/terminator/.thumbnails/large
rm -fv *.*
rm -fv *
echo "large thumbs deleted"
sleep 2	
echo
echo "deleting normal thumbs"
sleep 2
cd /
cd /home/terminator/.thumbnails/normal
rm -fv *.*
rm -fv *
echo "normal thumbs deleted"
sleep 2
echo
echo "deleting failed thumbs"
sleep 2
cd /
cd /home/terminator/.thumbnails/fail/gnome-thumbnail-factory
rm -fv *.*
rm -fv *
echo "failed thumbs deleted"
sleep 2
echo
echo "thumbnail cleanup successfull"
sleep 2



---

### Post by tswanee on 2007-07-04
> **alienexplorers said:**
> Your thumbnails are stored in the .thumbnails directory.  cleaning that will cause new pictures to be displayed.  I use a small script file to keep .thumbnails clean.
Ah, thanks! :D

---

