---
title: "Weird error when trying to open .jpg pictures"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by æþeling on 2006-09-20
Whenever I try to open a .jpg picture, I get the error message visible in the attachment. Also, instead of thumbnails, all .jpg pictures show as an icon with a green gnome foot.
If I right-click the picture and select to open it with gThumb (or whatever program), it works normally, but it's annoying to have to do it every time. Also, if I rename it to .jpeg, it opens normally, but I really don't have the time to rename every picture in my 2,7GB collection. So what could i do to make this dissapear?

---

### Post by hw-tph on 2006-09-20
Right-click on a .jpg file and select Properties. Click on the "Open With" tab and select what application you want to open it with (i.e. Gthumb).

I have had similar problems when I have uninstalled the default image viewer application.


Håkan

---

### Post by æþeling on 2006-09-20
That doesn't solve the problem (no matter which application I select to pen it with), it still display the error instead of opening when I double-click.

---

### Post by æþeling on 2006-09-20
just a bump back to first page

---

### Post by æþeling on 2006-09-20
bump...HELP ME!

---

### Post by kerry_s on 2006-09-20
Did you try renaming it to jpeg instead of jpg like the error says?

---

### Post by æþeling on 2006-09-20
> **kerry_s said:**
> Did you try renaming it to jpeg instead of jpg like the error says?

Yes, I did, but as I have already mentioned in the first post, I don't have the time or the will to rename every one of my 2,7 gigabytes of photos. There has to be another solution.

---

### Post by latecomer on 2006-09-20
When you rightclick on a .jpg file and select Properties and then the Open With tab, what does it say?

---

### Post by æþeling on 2006-09-20
It says "image viewer", but the picture still won't open with a double-click, no matter which app from the list I select.

---

### Post by æþeling on 2006-09-20
bump bump bump...

---

### Post by æþeling on 2006-09-20
b...b...b-b-b...bum...BUMP!

---

### Post by benfindlay on 2006-09-20
There is a batch rename command that you can use to rename tonnes of files at once, but I have no idea what that command is I'm afraid. Hopefully someone else does though...

---

### Post by benfindlay on 2006-09-20
Aha, after a short google search I have read that you can use gthumb to batch rename images in a particularly directory (no idea how though, never used gthumb)

You can also use the following link for a program called mvb which >  is a shell script written for BSD and Linux users, to "batch rename" files (change the name of many files at once) in the current working directory

Get it here:[http://linux.softpedia.com/get/System/Shells/mvb-16402.shtml]("http://linux.softpedia.com/get/System/Shells/mvb-16402.shtml")

Hope this helps

---

### Post by latecomer on 2006-09-20
have a look at this
[http://www.ubuntuforums.org/showthread.php?t=151650&highlight=jpg+error](http://www.ubuntuforums.org/showthread.php?t=151650&highlight=jpg+error)

---

### Post by æþeling on 2006-09-21
> **latecomer said:**
> have a look at this
[http://www.ubuntuforums.org/showthread.php?t=151650&highlight=jpg+error](http://www.ubuntuforums.org/showthread.php?t=151650&highlight=jpg+error)

That did it, thanks a lot.

---

### Post by MWAAAHAAA on 2006-09-21
Welcome to the wonderful world of Ubuntu. Suppose your files are in one directory. To rename all of the .jpg to .jpeg you just execute the following console commands from that directory:

rename 's/\.jpg$/\.jpeg/' *.jpg

For more info read the 'rename' man page.

---

