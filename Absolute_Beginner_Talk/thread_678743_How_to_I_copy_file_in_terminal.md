---
title: "How to I copy file in terminal?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by grebarton on 2008-01-26
Trying to copy file to a restricted folder but getting this in terminal:

grebarton@grebarton-desktop:~$ sudo cp/home/grebarton/Downloads/fm.exe* '/home/grebarton/.wine/drive_c/Program Files/Sports Interactive/Football Manager 2008' 
[sudo] password for grebarton:
sudo: cp/home/grebarton/Downloads/fm.exe*: command not found
grebarton@grebarton-desktop:~$ 

Any idea what I'm typing wrong?

---

### Post by RebounD11 on 2008-01-26
```
sudo cp /home/grebarton/Downloads/fm.exe* /home/grebarton/.wine/drive_c/Program\ Files/Sports\ Interactive/Football\ Manager\ 2008
```

It should be like this :d

By th way when you ope your terminal you are already in your home folder so the '/home/grebaton/' part can be left out... (only when you start the terminal)

PS: .wine is not a restricted folder .. it's just hidden - press Ctrl+H in Nautilus and it will show hidden files as well :D (and you won't have to use the terminal)

Good luck!

---

### Post by Paul820 on 2008-01-26
You need a space beween the **cp** and the path to the file
> sudo cp /home/grebarton/Downloads/fm.exe*

---

### Post by mikewhatever on 2008-01-26
There is a space between cp and location (udo cp /home/grebarton/Downloads/fm.exe*). Check out <man cp> for more info. I believe something like this should do the job: sudo cp /home/grebarton/Downloads/fm.exe* /home/grebarton/.wine/drive_c/Program\ Files/Sports\ Interactive/Football\ Manager\ 2008/.

What is fm.exe*? Could it be fm*.exe instead?

---

### Post by grebarton on 2008-01-26
Thanks so much mikewhatever

Only yours worked and yours was the last I tried but thanks still.

Can you just tell me why did you think to change the parts you did?

---

### Post by mikewhatever on 2008-01-26
> **grebarton said:**
> Thanks so much mikewhatever

Only yours worked and yours was the last I tried but thanks still.

Can you just tell me why did you think to change the parts you did?

Well, let's see. First, you must separate different parts with a space, that is <sudo cp /source /target>. The other thing was those multi word directories. The convention Terminal seems to use is word1 word2=word1 \word2/, not sure why.  In your case Program Files=Program\ Files/, Sports Interactive=Sports\ Interactive/, and lastly, Football Manager 2008=Football\ Manager\ 2008/. It's a little tricky, and I always try to avoid naming folders like that. You'd not need all the \\\, had you named the last one Football-Manager-2008 or similar, but without spaces. I guess there isn't much to do about Program Files.

---

