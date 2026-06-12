---
title: "File Extracting"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Edache on 2006-06-01
Hello,
Iam trying to extract a zip file to the usr/share/pixmap/gaim directory, but it says I do not have premission to do this. How can I extract this file into the gaim directory as root. Thanks:mrgreen:

---

### Post by IYY on 2006-06-01
The command is 

sudo unzip <filename> <location>

---

### Post by Edache on 2006-06-01
Thanks IYY I will give it a try.

---

### Post by nalmeth on 2006-06-02
Or if you're trying to use your graphical unzipper, try:
ALT-F2
gksudo file-roller

or whichever frontend you are using. You'll be prompted for the user password.

---

### Post by Edache on 2006-06-03
thanks nalmeth that worked for me, also thanks again IYY for you help.

---

