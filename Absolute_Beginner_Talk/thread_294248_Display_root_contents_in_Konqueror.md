---
title: "Display root contents in Konqueror"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2006-11-06
I'm not sure whether this is defaulted this way or not (I seem to recall seeing all the files in the /root directory at one point), but at this moment everything appears to be hidden except for the /home and /media directories. 

How can I display the rest of the directories, such as /opt, /usr, etc.

---

### Post by bailout on 2006-11-06
View->Show hidden files -  or similar term

---

### Post by LeslieL on 2006-11-06
I don't think that fixes the problem. Sometimes in Edgy I discover that I can see only /home and subdirectories, /root and subdirectories (if I'm running Nautilus as root), and /media. Showing hidden files just shows the hidden files in those directories. I have to log out and back in again to recover my ability to see all the other directories - /bin, /etc, /usr and so on.

---

### Post by esalvesen on 2006-11-06
There is a file called ".hidden in /".
Try "kdesu kate .hidden".

Good Luck.

Erik

---

