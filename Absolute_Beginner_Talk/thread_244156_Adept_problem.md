---
title: "Adept problem"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-08-26
I have updated my KDE to 3.5.4 and then I did the Adept update.  About half way through installing the updates, I got a message saying that there was a problem then it closed.  Now I can't use Adept at all!  I get the attached message every time I try to open Adept.

Can anyone help me fix this?

Russty.

---

### Post by Jucato on 2006-08-26
Try this:
1. Launch Konsole (K Menu > System)
2. type in this command:
```
sudo dpkg --configure -a
```
it should continue where it stopped installing.

---

### Post by Russty of Oz on 2006-08-26
WOW!  Thanks Fenyx!  That did the trick.  I don't know how I am going to remember all these things you have to do to make things work.  

That's one more problem over.  Now for the next one!

Russty.

---

### Post by Jucato on 2006-08-26
Glad I could help. :D

---

