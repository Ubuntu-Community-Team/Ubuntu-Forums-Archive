---
title: "Screen Resalution"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by trav777 on 2006-07-31
Hi all, I've got another question.

After using Automatix to install my nVidia Video Card Driver, I only have one choice for a screen resalution, the largest one (1920x1200) and it is frustraitingly large, everything is so small.  I used to be able to change it to 1280x800 which was perfect.

How do I fix this and get more choices for screen resalution sizes?

---

### Post by PaulFXH on 2006-07-31
Hi
Edit your xorg.conf file to include the resolutions you want.
You can follow the directions given by bluecherry in the thread.
Note, however, that there is an error in the first code in that the command is written twice (back to back). Just use "half" of this.

[http://ubuntuforums.org/showthread.php?t=224129](http://ubuntuforums.org/showthread.php?t=224129)

Good luck

Paul

---

### Post by OU812 on 2006-08-01
When I had problems, Dr. Nick posted this link

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

It has a lot of good stuff in it. But it does contradict bluecherry in one regard: It suggest using gksudo to edit xorg.conf instead of sudo. And based on my experience( read about it here [http://ubuntuforums.org/showthread.php?t=226219)](http://ubuntuforums.org/showthread.php?t=226219)), gksudo is the correct choice.

john

---

