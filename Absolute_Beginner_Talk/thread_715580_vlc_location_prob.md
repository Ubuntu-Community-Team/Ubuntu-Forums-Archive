---
title: "vlc location prob"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-05
how do i locate the c:\program files? i installed vlc for windows using wine(i got wine to work finally) and i cant seem to find the directory..

thanks

---

### Post by oedha on 2008-03-05
question : why do you have to install vlc for windows ?
program files will be under /media/sda1/Program Files......

---

### Post by gigaferz on 2008-03-05
inside  your home folder click on view hidden files  (ctrl+h) and folders, then find .wine if i understood correctly you will see your drive c:

---

### Post by lswest on 2008-03-05
yeah, it's under /home/<username>/.wine/drive_c/Program\ Files/

---

### Post by mikkko on 2008-03-05
thanks guys...

---

### Post by kpkeerthi on 2008-03-05
Why do you want to wine vlc when it can run natively in linux?

You can install vlc using
```
sudo aptitude update && sudo aptitude install vlc
```

Then Applications -> Sound & Video -> Vlc

---

### Post by mikkko on 2008-03-05
i didnt know it could run without using wine.. thanks for your info

---

