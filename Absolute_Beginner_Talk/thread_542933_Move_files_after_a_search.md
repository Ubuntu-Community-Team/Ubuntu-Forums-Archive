---
title: "Move files after a search"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-09-04
Hi,

I've got mp3 files in multiple directories and want to move them to a single new directory, I've search my drive for all mp3 files *.mp3 (using Search for files . .) and located everything and there doesn't seem to be a way of selecting all of these files and moving them to the new directory? 

J

---

### Post by jamvegan on 2007-09-04
The shift key is your friend. :)

To select all of the files first click on the top file in the list, then scroll to the bottom and, while holding down the shift key, click the bottom file in the list.  To move them all, open a file browser (for instance, by selecting Places->Home Folder) and make sure that the destination folder is visible in it (or if the folder is already visible on the desktop, skip this step).  Then, while holding down the shift key, click and drag the highlighted files from the search window to the destination folder.  (If you click and drag them without holding down shift, you will copy them instead of moving them.)

---

### Post by dwhitney67 on 2007-09-04
You can find all MP3s and run a command like this to move them to a particular folder (make sure the folder exists!!!!):

[FONT="Courier New"]$ find . -name "*.mp3" | xargs -r mv *folder*[/FONT]

Test it before you try it on your precious music files.

---

