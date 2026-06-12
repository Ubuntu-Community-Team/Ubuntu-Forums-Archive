---
title: "Desklets error"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by sk8trf69 on 2005-07-21
Im using Fluxbox and im trying to get desklets to work on my comp. i installed them...untard them....after u change the directory and do the ./configure i get this error
```

checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path

```

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=sk8trf69]Im using Fluxbox and im trying to get desklets to work on my comp. i installed them...untard them....after u change the directory and do the ./configure i get this error
```

checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path

```[/QUOTE]

gdesklets? The best way is to use synaptic to install them from teh backport server.

Hey...whats a beginner using fluxbox for? Did you read the stickied post at the top?

---

### Post by sk8trf69 on 2005-07-21
gdesklets is for Gnome isnt it?
i use fluxbox because its the best window manager in my opinion

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=sk8trf69]gdesklets is for Gnome isnt it?[/QUOTE]

Actually, its independent. And it works good on other platforms

> 
i use fluxbox because its the best window manager in my opinion

I understand. I was just wondering if you read this:

[http://www.ubuntuforums.org/showthread.php?t=35457](http://www.ubuntuforums.org/showthread.php?t=35457)

Beginners don't usually START with Fluxy.

(not that I'll slap you or move your post- I'm REALLY lenient unless someone is asking a question way over my head)

Just making myself clear.

---

### Post by rmjokers on 2005-07-22
If you choose not to use the gdesklets from the apt repository, it looks like (based upon the error message you posted) you need to install python.

apt-get install python

There may be other dependencies that gdesklets has that also need to be installed.  If you used the gdesklets version in the Ubuntu repositories, these dependency issues would be resolved automatically.

---

