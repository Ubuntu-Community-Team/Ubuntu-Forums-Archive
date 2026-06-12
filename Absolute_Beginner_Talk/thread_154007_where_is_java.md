---
title: "where is java?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by veighjay on 2006-04-02
hi

i did an apt-get install of the sun java (sunj2 re1.5). i installed it as instructed with all default options. now i would like to know where exactly the 'main' java file is (that's how beginner i am, i don't even know what to call the 'main' file). 
the reason i ask is that a program i'm trying to install (galleryremote for Gallery), is asking me to point out which java file i would like to use and where it is, and i don't know what to tell it!

thanks for your help....

---

### Post by localzuk on 2006-04-02
The easiest thing to do to install java is to follow the instructions at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

If you wish to find out where it is, try running ```
sudo updatedb[code] followed by [code]locate java | less
``` This will output the location of all files/directories with 'java' in their name - it is simply a case of looking for it in the list.

---

### Post by veighjay on 2006-04-02
thanks... found it... so if i have sun java installed, does it make sense to make it the default java program for everything? i followed some of the steps on [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) and realised that the 'gcj' java was default for most things...

---

### Post by taurus on 2006-04-02
Yes, you should make Sun's java 1.5 to be the default since gcj is the one from gcc...

---

### Post by veighjay on 2006-04-02
thanks... 

getting there, bit by bit....

---

