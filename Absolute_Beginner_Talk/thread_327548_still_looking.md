---
title: "still looking"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-29
is there a batch image resizer out there???

i found the renamer i just need them all to be the same size

---

### Post by meng on 2006-12-29
antgul: be more descriptive when you post. Take time, write longer posts, make sure that a reader will understand what you're looking for.

One easy way needs to have imagemagick installed, I'm not sure if it is installed by default, so try:
sudo aptitude install imagemagick

then look here
[http://www.novell.com/coolsolutions/tip/16524.html](http://www.novell.com/coolsolutions/tip/16524.html)
although beware that this solution will overwrite the original files.

EDIT
the command
convert
rather than mogrify, allows you to resize to a different filename, not sure how it works in batching though. You may need to combine convert with a shell script to do this safely.

---

### Post by ComplexNumber on 2006-12-29
> **antgul3382 said:**
> is there a batch image resizer out there???

i found the renamer i just need them all to be the same size
nautilus has an image resizer plugin. look in the repository for something like nautilus-plugin-imageresizer. thiis what you'll see in nautilus

---

### Post by bluedeer on 2006-12-29
GThumb Image Viewer (installed by default in Dapper - not sure about Edgy) will do batch resizing pretty easily/painlessly.

In gThumb, go to the directory where your pics are located, select all of the ones you want to resize, and select "scale images" from the Tools menu.  It'll let you set the various options before resizing the pics.  If you don't want to have to sit there and watch it, make a new folder for your resized pics before you start the resizing, and then select that as your destination folder.

---

### Post by antgul3382 on 2006-12-29
problem solved



how much more detailed than that can it get???   i got a lot of pictures i want to resize at once
hence batch image resizer

---

### Post by meng on 2006-12-29
Okay forget it just post however you like.

---

### Post by antgul3382 on 2006-12-29
hey im just givin you a lil ish guy sorry,   but anyways thanks guy/girls for all the help, all is well now

---

