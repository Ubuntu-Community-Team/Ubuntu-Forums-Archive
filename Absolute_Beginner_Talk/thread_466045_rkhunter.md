---
title: "rkhunter"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by TheFlamingBush on 2007-06-06
ive downloaded rkhunter, how do irun it again?.....ive tried sudo rkhunter in the terminal and it just seems to give me a read out of the parametres........

---

### Post by gerscht on 2007-06-06
mmh, [http://www.rootkit.nl/articles/rootkit_hunter_usage.html](http://www.rootkit.nl/articles/rootkit_hunter_usage.html) might help ;)

---

### Post by TheFlamingBush on 2007-06-06
thanks gerscht :)

bugger....i cant get the thing to work at all.....maybe its me, (definately its me! , who am i kidding!).........ive tried it a million different ways, ive got to inputting the command wrong, can someone post the command to help out a moron please! :-/

---

### Post by gerscht on 2007-06-06
Is it ignoring the given parameters?
if so, try a
```

sudo su
(password)
rkhunter

```

'sudo su' will give you a proper root console

---

### Post by TheFlamingBush on 2007-06-06
thanks gerscht finally got it to work with ```
 sudo rkhunter -c 
```

and im all clean which was a relief! :)

tried avg as well, but couldnt get the bugger to work properly, so ive gone back to clam, and firestarter....probably a little over protective, but its a work station as well and simply couldnt afford to replace my laptop! :)

---

