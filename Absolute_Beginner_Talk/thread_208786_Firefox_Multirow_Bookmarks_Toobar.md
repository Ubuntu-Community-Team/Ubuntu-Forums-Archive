---
title: "Firefox Multirow Bookmarks Toobar"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by TorxT3D on 2006-07-04
I got my windows firefox tweaked to where it has multirows (currently 3) of bookmarks on the toolbar instead of just one line.  The code for this should be put in the userChrome.css file.

I did this to the firefox linux userchrome, and its not working.  Does anyone know what file i need to edit?

this is the code

/* Multi-row bookmarks toolbar */

#bookmarks-ptf {display:block !important;}

#bookmarks-ptf toolbarseparator {display:inline !important;}

---

### Post by bollix47 on 2006-07-04
Using the following code in **userChrome.css **works for me in linux:

```
/* Multi-row bookmarks toolbar */
#bookmarks-ptf {display:block}
#bookmarks-ptf toolbarseparator {display:inline}
```

Note that the !important; code that you have is not used.

---

### Post by TorxT3D on 2006-07-04
umm, still doesnt work.
this is the correct file and directory right?

> cd /usr/share/firefox/defaults/profile/chrome
> sudo gedit userChrome.css

---

### Post by bollix47 on 2006-07-04
No that's not the correct folder.

It will be in your home folder under .mozilla/firefox/XXXXXX.default/Chrome

XXXXXX will be a random set of numbers 

You can get the chromedit or MR Tech's Local install extension.  Both will edit the correct file.

---

### Post by TorxT3D on 2006-07-04
thanks buddy, i used mr techs extension, now that i know where its at, i'll just remove the extension.

---

