---
title: "Firefox opens home folder not home page"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by da Wookiee on 2008-02-27
Whenever I open Firefox, it opens a directory to my home folder, not my home page.  Can anyone tell me why this is happening and how to fix it.  I just got all the plugins installed and really don't want to remove and reinstall unless I have to.  I did try changing the video card today, but don't know how that might have caused a glitch, since I had to change it back (another post).

---

### Post by santiagoward2000 on 2008-02-27
> **da Wookiee said:**
> Whenever I open Firefox, it opens a directory to my home folder, not my home page.  Can anyone tell me why this is happening and how to fix it.  I just got all the plugins installed and really don't want to remove and reinstall unless I have to.  I did try changing the video card today, but don't know how that might have caused a glitch, since I had to change it back (another post).

Hi!
One question: how are you opening Firefox? Have you created a desktop launcher or something? If so, perhaps the launcher's exec may be wrong. Try to right click on it, choose edit and make sure the exec or command says just: ```
firefox
```
Cheers!

---

### Post by LuisGMarine on 2008-02-27
Or just open up firefox and go to

*Edit > Preferences* and under **"home page "** have it to something like *[www.google.com](www.google.com) *instead of a file path ...

hope this helps!  

Duces!

---

### Post by Dr Small on 2008-02-27
> **LuisGMarine said:**
> Or just open up firefox and go to

*Edit > Preferences* and under **"home page "** have it to something like *[www.google.com](www.google.com) *instead of a file path ...

hope this helps!  

Duces!
about:blank is a faster home page ;)

---

### Post by LuisGMarine on 2008-02-27
Very true, but internet sucks on Military barracks, so opening straight to google lets me know if I have internet or if I have to read a book for the rest of the night ... :)

---

### Post by santiagoward2000 on 2008-02-27
> **LuisGMarine said:**
> Or just open up firefox and go to

*Edit > Preferences* and under **"home page "** have it to something like *[www.google.com](www.google.com) *instead of a file path ...

hope this helps!  

Duces!

Hi!
The thing is that if there's something in the command after **firefox**, no matter what your home page is, you won't get there. For example, if it says **firefox 0** (which is a common problem with Kiba-Dock) you will get a blank page, and its address will be 0 (you will actually see [http://0](http://0) in the address bar).

---

### Post by da Wookiee on 2008-02-27
I'm launching it from a media key.  It worked this morning, I'm not sure what changed.  I tried launching from the menu, and it loaded cnn's webpage like it's supposed to.

tried changing the launcher, but that only changes the button pushed for the action, not the command.

---

