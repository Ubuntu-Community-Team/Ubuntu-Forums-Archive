---
title: "&quot;timestamp too far in the future&quot; in Xubuntu"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by n_nous on 2006-10-25
Hy all, I was trying to change my time settings in xubuntu through the command line (please tell me there's another way) and I accidentally set it to a date in the past. 
Now I can't use sudo. I get the message "timestamp too far in the future".
I searched the forum and found out that this guy had the same problem:

[http://ubuntuforums.org/showthread.php?t=173505](http://ubuntuforums.org/showthread.php?t=173505)

BUT he had the luxury of gnome or kde's adjust date/time

what am I supposed to do? I can't use sudo now, meaning I can't change date/time from the command line. This is really frustrating. And I'm starting not to like xfce any more. I don't know what in the world stopped them to implement adjust date/time in the Properties Menu of the clock.

---

### Post by deadgobby on 2006-10-25
Did you try the same thing as the thread post? Lunix is linux, you are using a different desktop envioment.
Gobby

---

### Post by n_nous on 2006-10-25
well I don't think that xfce has an adjust date/time application (that was the solution in the thread). That's why I was in the command line in the first place. I was using ```
sudo date -s STRING
```, but I can't do that again, I can't use sudo ](*,)

---

### Post by aysiu on 2006-10-25
You may find [this thread](http://www.ubuntuforums.org/showthread.php?t=162376) helpful. I know I did.

---

### Post by Bachstelze on 2006-10-25
Just run *sudo -k* to reset your timestamp. I never faced the problem myself but I reckon it should do the trick.

---

### Post by n_nous on 2006-10-25
well.. I solved the problem by myself.. in a very unexpected way.. I opened another terminal.. and in this new terminal sudo worked..

---

### Post by kerry_s on 2006-10-25
Does xubuntu have ntpdate installed? If so does rebooting not adjust the time from the internet?

---

### Post by az on 2006-10-25
> **kerry_s said:**
> Does xubuntu have ntpdate installed? If so does rebooting not adjust the time from the internet?

Not if your internet connection is not yet configured.

---

