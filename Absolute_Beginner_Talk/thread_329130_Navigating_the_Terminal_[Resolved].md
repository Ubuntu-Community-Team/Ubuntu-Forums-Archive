---
title: "Navigating the Terminal [Resolved]"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-01
Whenever I use cd to move to a folder with more than one word as its title, the terminal only reads the first word of the title. What can I do to make the terminal read the next word(s)?

---

### Post by Sef on 2007-01-01
Be sure and not make spaces.   Could you post what you are trying to do?  That way any errors could be picked up, if it is something else.

---

### Post by wersdaluv on 2007-01-01
I want to get inside the folder /home/user/Extracted Files/Audacious.

Whenever I use "cd Extracted files" while I am under "/home/user," the terminal reads it as Extracted and as expected, I won't get in the Extracted Files directory.

---

### Post by ciscosurfer on 2007-01-01
> **wersdaluv said:**
> I want to get inside the folder /home/user/Extracted Files/Audacious.

Whenever I use "cd Extracted files" while I am under "/home/user," the terminal reads it as Extracted and as expected, I won't get in the Extracted Files directory.You need to use the backslash to inform the terminal of a space.  So, you can either you tab completion to finish out the full directory (cd /home/username/E<tab>) or you can finish it out yourself like this:```
cd /home/username/Extracted\ Files/Audacious
```

---

### Post by aysiu on 2007-01-01
Type ```
~/Extrac
``` and instead of hitting **Enter**, hit **Tab** twice.

---

### Post by bukwirm on 2007-01-01
Also, you can enclose any name with spaces in it in double quotes, like so:

 cd "Extracted Files"

---

### Post by psycho78 on 2007-01-01
... or embrace the path with " " , it should autocomplete correctly this way....
e.g.:  cd "/home/user/this is a test" , hit TAB after this.....

---

### Post by wersdaluv on 2007-01-01
Wow... So there's a lot of ways and means.

Thank you! :)

---

