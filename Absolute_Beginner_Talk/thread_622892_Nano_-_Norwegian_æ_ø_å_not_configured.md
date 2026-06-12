---
title: "Nano - Norwegian æ ø å not configured ?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bewire on 2007-11-25
[See last post for resolution]

Hi, I just realized that my nano editor don't allow me to enter æ ø å. It works fine at the shell console so  I guess that I have missed a configuration parameter in nano. Can someone give some advice or point me to the relevant docs ? 

Please give me a hint if this has been addressed in another thread. I tried several searches.

NOTE: I'm running the ubuntu server without GUI.

---

### Post by bewire on 2007-11-26
Hi, this is how æøå looks in nano.

---

### Post by mali2297 on 2007-11-26
Post the output of
```

locale

```

Do you connect to a server through PuTTY or similar?

---

### Post by bewire on 2007-11-28
Here is the output of locale:


```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

I see there's no reference to Norwegian (no). So I guess this is a good clue to my problem.

You are absolutely rigth, I'm using Putty to connect to the Ubuntu Server from my XP desktop.

---

### Post by mali2297 on 2007-11-29
This might help:
[http://my.opera.com/Mr%20Green/blog/show.dml/146230](http://my.opera.com/Mr%20Green/blog/show.dml/146230)

If you manage to solve it, tell us how.

---

### Post by bewire on 2007-12-11
Hi, I just changed the settings in Putty (Window->Translation) to UTF-8, and æøå is now working. Thanks :-)

---

