---
title: "how can I copy to this file?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-10-28
HI

I want to copy some things to a file but it wont let me just copy it, so I guess I have to do it through the terminal, but I still haven't got the hang of exactly what to put in there.

I have some images in /home/russty/photos   and I want to copy them into  
/usr/lib/firefox/defaults/profile/chrome

So in the terminal I will need to start with sudo but how do I tell it what to copy and how to copy it to that file?

Russty:)

---

### Post by tonyr1988 on 2006-10-28
> sudo cp -r /home/russty/photos /usr/lib/firefox/defaults/profile/chrome

cp = copy
-r = recursively (copy the folder and all files in it)
/home.../photos = "from"
/usr.../chrome = "to"

That should work for you.

Alternatively, for a graphical way, do this (if you're using GNOME):

> gksudo nautilus

Navigate to /home/russty. Right-click "photos" and click Copy.

Navigate to /usr/lib/firefox/defaults/profile/chrome. Right-click an empty space and click Paste.

---

### Post by Russty of Oz on 2006-10-28
Thanks Tony, that was just what I needed.  Something else to write down in my little Linux How To book!:D

---

