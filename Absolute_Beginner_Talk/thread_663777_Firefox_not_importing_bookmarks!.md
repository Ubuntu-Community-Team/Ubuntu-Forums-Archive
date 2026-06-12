---
title: "Firefox not importing bookmarks!?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by ftaylor on 2008-01-10
I just changed from ubuntu 32bit to ubuntu 64bit as I realised my laptop could support it.

I saved the bookmarks.html file from the firefox/prefs folder. When I try to import it in firefox it just adds some standard ubuntu links and not my bookmarks? What's the problem with it? Anyone know?

I've done this before when going from 32 to 32 bit (when windows messes up, every few weeks) and the import has worked no bother.

---

### Post by skroops on 2008-01-10
Take a look at the bookmarks.html file.  Are the right bookmarks in that html file?  Perhaps you didn't export what you wanted.

---

### Post by philinux on 2008-01-10
Your bookmarks would have been stored in

/home/yourusername/.mozilla/firefox/xxxxxx.default/bookmarks.html

where xxxxxx is a bunch of random characters.

---

### Post by Hospadar on 2008-01-10
if you just double click the html file it will open up in firefox as a web page and you can see what all links are in it.

Note if you are looking for the toolbar links at the top of the page, those don't get imported right. if you go to Bookmarks->manage copy all the stuff out of the second "bookmarks toolbar" folder into the topmost "bookmarks toolbar" folder

---

