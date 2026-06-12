---
title: "Directories"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Witling on 2008-01-24
I want the root user's instance of Firefox to use the bookmarks in my ordinary user   account, I know the file names and I know the Firefox file I have to modify. For this example let's call the root user Jones and the ordinary user Smith.

If I modify Jones' PROFILES.INI  to point to Smith's profile, will Linux, and Ubuntu in particular, alllow the superuser Jones to use Smith's profile? And from time to time I might want to modify Smith's bookmarks while logged on as Jones.

Second, assuming that Jones will be allowed to access Smith's profile, what is the proper form for the path? Specifically, do I have to include the hard drive in the path? Would the path look like

smith/mozilla/firefox/xxxxxxxx.default  or
/smith/mozilla/firefox/xxxxxxxx.default or yet some other configuration?

---

### Post by Rocket2DMn on 2008-01-24
You should use the full path starting at the root of the filesystem, like
/home/smith/.mozilla/firefox/xxxxxxxxx.default
^ note the "." in front of mozilla since it is a hidden folder.  You will need to check the correct file to use, I'm not sure if you want that xxxxx.default or the profiles.ini file.

You will be able to read/write the file as root.

Another option is to setup Foxmarks which synchronizes your bookmarks on a server so you can access them from multiple computers, dual boots, or multiple  user accounts on one computer.

---

### Post by emarkd on 2008-01-24
If Jones is really a superuser account, it can read and write whatever it wants to.  I'll spare you the speech about how dangerous it is to run as root, but if you didn't know this was dangerous, it is.

Your paths will most likely all begin from /home, so in your example using the truncated paths you provided, the profile would actually reside in:

/home/smith/mozilla/firefox/profiles.ini

and then /home/jones/mozilla/firefox/profiles.ini would link back to it.

---

### Post by Witling on 2008-01-24
Thank you, you've answered my question.

Yes, I know it's dangerous to routinely operate as a root user but from time to time I want to track something down and install it as a root user. I want any bookmarks I develop to be saved into the account that I ordinarily use.

---

