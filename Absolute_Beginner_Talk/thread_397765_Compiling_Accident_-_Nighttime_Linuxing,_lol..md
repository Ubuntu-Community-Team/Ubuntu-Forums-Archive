---
title: "Compiling Accident - Nighttime Linuxing, lol."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by InuyashaDuelist on 2007-03-31
Well, I've been trying to get Wesnoth 1.3.1 installed on Kubuntu for the last couple of hours.

I tried to find a place to get the debian files for it, and found [this]("http://www.wesnoth.org/forum/viewtopic.php?t=9679") guide. I just followed it, as it was normal compiling, but I accidentally took the following line and used it literally:

```
 ./configure --prefix=/home/yourusername/games/wesnoth/ --enable-editor
```Now I have an extra folder in my /home directory called 'yourusername', and no wesnoth. How can I get rid of this folder, and how can I move wesnoth over without re-making it again? (I hate waiting for two hours. -_-)

Thanks in advance.

-Inu'

---

### Post by InuyashaDuelist on 2007-03-31
Bumpity.

I've managed to get version 1.3.1 installed in the correct place, so now i'm just interested in getting rid of that darn extra folder in my /home directory.

---

### Post by yabbadabbadont on 2007-03-31
Can you not simply delete it?  If you get errors when you try to, open a terminal window and run:
```
rm -rf ~/yourusername
```

---

### Post by InuyashaDuelist on 2007-03-31
Doesn't work, already tried it. Just a bunch of 'Permission Denied' errors.

Apparently, I can't get rid of the Wesnoth folder.

---

### Post by yabbadabbadont on 2007-03-31
Then add sudo to the front of the command.

---

### Post by InuyashaDuelist on 2007-03-31
Oh, of course!

Why thank you, problem solved. :)

---

