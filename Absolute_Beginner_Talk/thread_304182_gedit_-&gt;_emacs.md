---
title: "gedit -&gt; emacs"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-11-21
Hi!

I'm pretty new in using emacs. When I've written a file (.tex) in gedit and opens it in emacs every line ends with "^M". Does anyone know why?


Regards Sabrina

---

### Post by sabrina on 2006-11-21
BTW. Does anyone know how to change the fonts in emacs to something more readable?

---

### Post by skymt on 2006-11-21
The ^M problem means that the file you're editing is in DOS format, so it has some extra junk at the end of each line. To solve it, install the "tofrodos" package and run "fromdos" on the file.

As for the font, there's not much you can do. The stable version of emacs doesn't support antialiasing. If you want to try a testing version that does, check out the [howto here](http://ubuntuforums.org/showthread.php?t=126023).

---

### Post by sabrina on 2006-11-21
Thank you for the quick and precise answer! :)

---

### Post by sabrina on 2006-11-22
Unfortunately the other thread's guide doesn't work anymore (as is also written on page 9). Does anyone know another way to fix the problem with emacs' fonts?

---

