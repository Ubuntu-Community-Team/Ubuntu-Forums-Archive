---
title: "Real dumb question, but what does ~ stand for?!"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by kimangroo on 2008-01-30
This is really basic linux stuff, but what does ~ stand for.

ie when typing a location ~/ .something

Does it stand for the /home/username location?

Tried googling it, but you can't search for "~"!

Thanks

---

### Post by jeffus_il on 2008-01-30
Your home folder.
In your post ~/ .something would be /home/[kimangroo]("http://ubuntuforums.org/member.php?u=479244")/.something
~ becomes /home/[kimangroo]("http://ubuntuforums.org/member.php?u=479244")

By the way, it's not a dumb question, only an interested mind asks questions. The dumb ones never asked. Ask a "dumb" one every day and by the end of the year you'll be an expert.

---

### Post by LaRoza on 2008-01-30
There are a few others you'll see:

~ == home directory
.. == parent directory (one directory up)
. == this directory

If you have a file in "/home/laroza/script.py" the following are all point to it:

```

~/script.py
./script.py
../script.py IF you are in a directory below it, like /home/laroza/Desktop

```

To find your current working directory, you can type "pwd" in the terminal.

---

### Post by kimangroo on 2008-01-30
Thanks a lot guys, that makes some sense now.

[quote=jeffus_il]By the way, it's not a dumb question, only an interested mind asks questions. The dumb ones never asked. Ask a "dumb" one every day and by the end of the year you'll be an expert.[/quote]

Expect plenty more *dumb* questions from me in the future then! :)

---

### Post by erfahren on 2008-01-30
actually, if you forget your name, you can type "whoami" in the terminal. - seriously - lol

anyway, I did some of this course when first starting Linux - it's pretty good if you're interested. [http://www.linux.org/lessons/index.html](http://www.linux.org/lessons/index.html)

this site is also handy: [http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by bumanie on 2008-01-30
~ is called a tilde sign. It is used sometimes to denote changing directories and sometimes to indicate something has been backed up. I am open to more information, if anyone has anything to add.

---

### Post by hyper_ch on 2008-01-30
the tilde sidn is also used in spanish and portuguese for different pronounciation of letters.

---

### Post by jeffus_il on 2008-01-30
My aunt's name is Ma~

---

### Post by Hugo Galvão on 2008-01-30
You can also use it for any user's home directory, not just yours, if you use
```
 ~/ 
```
you are referring to your own (logged in user) home directory, but you can also use something as
```
 ~thisuser/
 ~thatuser/ 
```
to access different home directories of different users, so '~thisuser/' = '/home/thisuser/', and '~thatuser/' = '/home/thatuser/'

---

### Post by LostMagix on 2008-01-30
I Just found out what it means to, your not alone.

---

