---
title: "Where is it?!?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-14
i just installed Armagetron Advanced using...
>  
[http://www.getdeb.net/app.php?name=Advanced%20Armagetron](http://www.getdeb.net/app.php?name=Advanced%20Armagetron) 

the program works perfectly, but i can't find where it installed.  i want to do some modding, but can't get to the files!!!  please help!

---

### Post by Kobalt on 2007-05-14
Have you tried launching it with Alt+F2, *name-of-the-app* ?

---

### Post by locke.dragon on 2007-05-14
i can get it to run, i just want to find the files so i can modify the game (textures and such).

---

### Post by srt5 on 2007-05-14
pop open a terminal and type 
```
locate armagetron
```
It will output the paths of where the package is installed. Hope this helps :)

---

### Post by locke.dragon on 2007-05-14
that actually didn't do anything.  but i did find it in...
> 
/usr/share/games/armagetronad

thanks for the quick feedback!  :D

---

### Post by srt5 on 2007-05-14
Glad you found it :) the reason it didn't find it is because i forgot to put the "ad" at the end.

```
locate armagetronad
```

should work.

---

### Post by RSingh on 2007-05-14
Use slocate.

Do: 
```
slocate -u
```

then:
```
slocate <name of file>
```

---

### Post by locke.dragon on 2007-05-14
thanks for the advice, but the only way i got it working was 
```

locate [armagetronad]

```
thanks anyway!  ;)

---

