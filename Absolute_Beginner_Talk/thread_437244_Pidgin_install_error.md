---
title: "Pidgin install error"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-05-08
ok...this makes no sense. i tried even running the  console install way, and then tried the .deb itself. same error every time...

---

### Post by silentjudas on 2007-05-08
actually here is a better pic

---

### Post by silentjudas on 2007-05-08
no one?

---

### Post by y-lee on 2007-05-08
I installed pidgin from the source code found on their web site and had no problems. Where did ya get the deb? If ya want to try the source code I followed the instructions in the Install file found there except I used **sudo make install**. i'm new to ubuntu so sorry this is not much help.

---

### Post by shanike on 2007-05-09
i've tried to compile pidgin on my own but appearently it didn't work out > after installation i was able to run the application by alt+f2... it ran for about 10 seconds. now i can't run pidgin in any way, buddy list pops out for approx. 2secs and then disappears. i tried to reinstall it using various .debs, no luck either :(

---

### Post by zvacet on 2007-05-10
I know this is not popular thing to do but if you want you can try this 

[http://www.getdeb.net/search.php?keywords=pidgin]("http://www.getdeb.net/search.php?keywords=pidgin")

---

### Post by Kobalt on 2007-05-10
If you want to compile it I recommend this way : ```
sudo apt-get build-dep gaim
./configure
make
sudo make install
```
I've done it this way and it works flawlessly...

---

