---
title: "firefox &amp; bookmarks"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-06-06
Is it possible to point firefox on Ubuntu and Windows to read from the same bookmark file?
thanks

---

### Post by steeleyuk on 2007-06-06
You can use the Bookmark Manager to import the bookmarks file.

---

### Post by Mazen on 2007-06-06
i know i can import the file but i don't want to keep importing and exporting from one to the other, i want to add bookmarks in one and have them appear in the other, well basically firefox should be reading and writing to a file i just want to know if i can make that file common!

---

### Post by Ferri on 2007-06-06
You may try to make a symbolic link from windows bookmarks.html file to the folder you have the same file in ubuntu. You'll need to have write access to the windows drive.

---

### Post by steeleyuk on 2007-06-06
I don't think Firefox can update its bookmarks dynamically, unless theres an extension out there that does it.

Edit: actually it can, see above.

---

### Post by aidanr on 2007-06-06
[https://addons.mozilla.org/en-US/firefox/search?q=sync+bookmarks](https://addons.mozilla.org/en-US/firefox/search?q=sync+bookmarks)

---

### Post by tschuliaen on 2007-06-06
I use the Firefox-Plugin [Foxmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410"). It works perfect for me and I'm working with 3 Computers with Linux and Windows

---

### Post by logos34 on 2007-06-06
> **aidanr said:**
> [https://addons.mozilla.org/en-US/firefox/search?q=sync+bookmarks](https://addons.mozilla.org/en-US/firefox/search?q=sync+bookmarks)

But will it work with firefox 2.0?  There's a newer version called sync and sort [here]("https://addons.mozilla.org/en-US/firefox/addon/2367").  But that's via an ftp server...I think what the poster is after is something like the symbolic link thing...I know that firefox bookmarks in winxp pro is located in Documents and Settings/Administrator/Application Data/Mozilla/Firefox/Profiles/yourprofile.default (and not in the program folder).

---

### Post by steeleyuk on 2007-06-06
the Firefox profile directory is located at:

/home/<username>/.mozilla/firefox/<random_string>.default

there is a bookmarks.html file in there which stores the bookmarks for Firefox

---

### Post by logos34 on 2007-06-06
I've been wondering about this issue too, but in my case I don't think I can use the symbolic link route because my x64 edition of XP pro is not supported by fs-driver andthe sym link can't be stored on fat32 or ntfs.

---

### Post by Rocket2DMn on 2007-06-06
To me, foxmarks looks the best.   Anybody have any other input on that plugin?

---

### Post by silkstone on 2007-06-06
Foxmarks is ideal and works with the latest Firefox 2.0.0.4. It syncs via a web server and you can set it to do this automatically, so it keeps the bookmarks up-to-date on all machines that have Foxmarks installed.

---

### Post by logos34 on 2007-06-06
Just installed it, nice 'lil addon.  Since I can't seem to link my bookmarks across filesystems on my drives, it'll have to do (but I for one try to avoid this online stuff like clipmarks, etc--they analyze your links and other nonpersonal info anonymously "in aggregate" and then sell it to marketers no doubt.  The world is for sale.).

---

