---
title: "where to put a startup script"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by gogogadgetearl on 2005-11-07
I'm following [this HOWTO](http://www.linuxquestions.org/questions/history/108737) on side mouse buttons, and it recommends that you create a few startup scripts.  Where on Kubuntu should these be put?

---

### Post by adwait on 2005-11-07
Put them in /etc/init.d/. Then use
```
sudo rcconf
``` 
and check the box against the appropriate script to run it on every boot. Make sure the files are executable.
If you get a command not found on rcconf use
```
sudo apt-get install rcconf
```

---

### Post by patrick295767 on 2005-11-07
I got this reply ... 
  
[http://www.ubuntuforums.org/showthread.php?t=86453](http://www.ubuntuforums.org/showthread.php?t=86453)
  
See ya'
  
Pat'

---

