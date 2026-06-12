---
title: "hello"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-09-05
my computer will recognize everything except my dvds ive installed the codecs is there something im not doing right when i try to play the movie with xine it says theres not a plugin to handle dvds

---

### Post by RomeReactor on 2007-09-05
Hi. Read [this first]("https://help.ubuntu.com/community/RestrictedFormats"). If after reading that you agree to install the needed packages, then you're going to need the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories and **libdvdcss2**. For that, take a look [here]("http://ubuntuforums.org/showthread.php?p=3300453#post3300453").

---

### Post by softtower on 2007-09-05
```
sudo apt-get install libdvdread3 libdvdcss2
```

---

