---
title: "music files say error O_O"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
ERROR: you do not have the right plugins to decode this media file, or something like that, then it says, you must install missing plugins,, i dont know how to install things.. what do i do?

---

### Post by MenZa on 2007-08-09
You have to install the gstreamer plugins; for pretty extensive media support (wmv, mp3, aac etc., etc.), run the following command:

```
sudo apt-get install gstreamer0.10-plugins-*
```.

---

### Post by jake16424 on 2007-08-09
> **MenZa said:**
> You have to install the gstreamer plugins; for pretty extensive media support (wmv, mp3, aac etc., etc.), run the following command:

```
sudo apt-get install gstreamer0.10-plugins-*
```.

thankyou very much =) now do i have to do the backspace + ctrl + alt?

---

### Post by MenZa on 2007-08-10
Nope. It should work as it is; Plug'N'Play. :)

---

