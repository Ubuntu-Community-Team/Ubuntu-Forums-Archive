---
title: "Moving Files From Many Folders To One"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2007-11-15
I accidentally deleted a folder with a bunch of pictures and movies of my kids.

I used Photorec to try and get them back. It worked great! Unfortunately, from the 80GB partition it went through, it ended up retrieving over 300 folders containing 500 files each (mostly .txt files containing tiny snippets of code -- for what, i don't know!).

What I'd like to do is move all the files into one folder so I can arrange them by filetype and pick out the .jpg and .mov files I want to keep and ditch the rest. I don't want every single .jpg because most of the jpegs found by Photorec are irrelevant things I deleted from the drive years ago. I just want to browse through the files and pick the ones I want, but that's a pain in the rear if I have to search through 300+ folders.

I tried playing around with grep, find, search, mv, etc etc, but my (incredibly amateur) bash skills are apparently not up to the task!

If someone has a solution I'd be eternally grateful!

---

### Post by Angus77 on 2007-11-15
bump

---

### Post by jfinkels on 2007-11-15
Assuming there are no spaces in the filenames, you could do something like```
for I in `find */path/to/folder/with/files/in/it* -type f `; do mv $I */some/destination/folder*; done
```

NOTE: I HAVE NOT TESTED THIS.

---

### Post by Angus77 on 2007-11-15
It worked!

Thank you so much!

---

### Post by jfinkels on 2007-11-15
Wow! Lucky :D.

You could even have done something like "find only files ending in .jpg, .mpg, .mp3, whatever"...Remember, Linux has an elegant solution to just about every problem :)

---

