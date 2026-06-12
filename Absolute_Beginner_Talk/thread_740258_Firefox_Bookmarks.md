---
title: "Firefox Bookmarks"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Punkristo on 2008-03-30
My sister did something to my computer that messed up my Ubuntu installation so Im gonna reformat the drive and reinstall it. I can save all my info in the drive but I dont know how to get back all the bookmarks that I had in my Firefox. I cant run Ubuntu so I cant export the bookmarks like that. Are the bookmarks saved in a file in the drive?

I found a few bookmarks.html but they have the default bookmarks which mozilla firefoz comes with, but not the bookmarks that I had.

---

### Post by kellemes on 2008-03-30
> **Punkristo said:**
> My sister did something to my computer that messed up my Ubuntu installation so Im gonna reformat the drive and reinstall it. I can save all my info in the drive but I dont know how to get back all the bookmarks that I had in my Firefox. I cant run Ubuntu so I cant export the bookmarks like that. Are the bookmarks saved in a file in the drive?

Blame you sister?  ;-)

In my case the profile folder is in ~/.mozilla/firefox
There is a folder in there called "somestring.default", that's where the default profile is..
You can simply copy it back this location when you installed firefox and import the profile like so..

from terminal:
```
firefox -profilemanager
```
point the default profile to this profiledirectory.

Edit: Not sure where firefox stores it's data in Ubuntu, just browse the home folder and watch for folders (hidden so starting with a dot) that holds the firefox profile.

---

### Post by TrikeKid on 2008-03-30
Nevermind, kellemes beat me to it.

---

### Post by Punkristo on 2008-03-30
Never mind I found them here:

\home\USERNAME\.mozilla\firefox\05op7x29.default

---

### Post by Duck2006 on 2008-03-30
If you want to do it manual, open your home folder,
hold Ctrl and the h key,
that will show the hidden folders,
find the .mozilla folde,
and click the folder to open firefox,
and the same for lse3eiuy.default,
and you will find your bookmarks.html
in there.

---

### Post by Punkristo on 2008-03-30
Thanks for the help everybody

---

