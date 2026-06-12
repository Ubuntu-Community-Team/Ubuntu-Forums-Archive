---
title: "Firefox bookmarks"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-05-05
I had a problem with a /home partition (separate post--don't want to deal with it here, but y ou can view the thread for that problem here:

[http://ubuntuforums.org/showthread.php?t=433690](http://ubuntuforums.org/showthread.php?t=433690)

Anyway, what I need for a quick fix is this: I need to get my Firefox bookmarks from the other /home folder on that other partition that isn't used (but it is mountable and all files seem to be there) to the default place where Ubuntu installs Firefox under my personal folder in the / partition.

I was able to get my Windows email program working again under wine after copying that folder to where it would be in the / partition. So that's one of the two main things I needed back and have half of the problem licked. Well, almost half, but the two most important ones anyway. 

So, where would I find the bookmarks file or folder?

It's not as simple as copying the folders under /mozilla. I tried that and it didn't do anything. 

Donald

---

### Post by Happy_Man on 2007-05-05
Well, in /home/<your name>/.mozilla/firefox, there will be a folder with a name that looks something like: 40o8a7es.default. Go into there, and copy the bookmarks.html file into the new folder, and restart Firefox. Hope this helps!

---

### Post by ubnewbie2 on 2007-05-05
or rather than copy the file, you can import it using Firefox's Bookmarks> Organise Bookmarks...

---

### Post by t2000kw on 2007-05-05
It worked. Thank you. I copied the file into the new location. I also put a copy on the desktop. It's a quick way to look through the list (though it won't update itself).

---

