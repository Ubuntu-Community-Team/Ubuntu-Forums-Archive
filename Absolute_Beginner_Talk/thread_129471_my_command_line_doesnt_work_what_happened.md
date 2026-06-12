---
title: "my command line doesnt work? what happened?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-13
Hi, well i started up my ubuntu, but now my commands no longer work in the terminal.

cd, dir, whereis, locate, etc....are not working. suggestions?

---

### Post by aysiu on 2006-02-13
Can you be more specific? When you say "not working," what errors exactly do you get?

---

### Post by bbqbaker on 2006-02-13
ex:
koloa@ubuntu:~$ dir
bash: dir: command not found

???? working fine yesterday.

---

### Post by aysiu on 2006-02-13
Maybe [this](http://64.233.179.104/search?q=cache:UNRnh0M7fyMJ:www.solurix.net/forum/index.php%3Fshowtopic%3D177845%26mode%3Dlinearplus+%22bash:+dir:+command+not+found%22+linux&hl=en&gl=us&ct=clnk&cd=7&lr=lang_en) might help.

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=bbqbaker]ex:
koloa@ubuntu:~$ dir
bash: dir: command not found

???? working fine yesterday.[/QUOTE]
Did your command PATH somehow get changed so it doesn't include /bin?  Try 
```

$ echo $PATH.

```

---

### Post by bbqbaker on 2006-02-13
hi, thanks for posting the links.

i typed this:
PATH=$PATH:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/local/bin:/usr/bin:/usr/X11R6/bin:/root/bin

and now it works. what happened, why did it get messed up? will I have to run this everytime i start ubuntu?

thanks again!

---

