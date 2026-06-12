---
title: "How to quit/abort software installation"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mikewhatever on 2007-01-31
Suppose I waned to install something like Amarok, but the download rate was so slow, that I changed my mind and decided to quit. Is there a way to do it nicely, or do I simply close the terminal? What happens to the libraries that finished downloading?

---

### Post by ComplexNumber on 2007-01-31
don't you see a cancel button? also, what are you using to download?

---

### Post by mikewhatever on 2007-01-31
No, no cancel button. I've tried it in the terminal, ```
sudo apt-get install amarok
```and some KDE libs were needed. The home line is 1.5 Mbits.
I'll edit the title in a minute.

---

### Post by ComplexNumber on 2007-01-31
you can open up the system monitor and kill the process.

---

### Post by raul_ on 2007-01-31
Ctrl+c ? that stops processes in the command line, i don't know if it's clean though. I think it is. You may have to do a clean or remove the software again. If it's still dowloading, then there's no problem. because ultimately you'll get the files in the cache so that if you decide to install them later, you don't have to download the whole file

---

