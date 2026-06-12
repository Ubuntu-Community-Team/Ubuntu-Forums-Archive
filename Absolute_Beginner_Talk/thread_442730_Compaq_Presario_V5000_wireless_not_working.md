---
title: "Compaq Presario V5000 wireless not working"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by SUBS0nic on 2007-05-13
Hello all, I just installed ubuntu on my laptop and for the life of me cannot get the wireless to work, i have tried to look for the driver but could only find articles by people looking for the same answer, i like to travel with my laptop so i need the wireless to work. im not sure what i'm supposed to offer in the terms of info so just ask me what you think should help and ill try to answer, this si my first linux try so forgive the newbness . also thanks in advance

---

### Post by Bachstelze on 2007-05-13
In a terminal, run :

```
lspci -n | grep $(lspci | grep Network | awk '{print $1}') | awk '{print $3}'
```

and paste what you get, it should be eight hex digits with a colon in the middle.

---

### Post by overdrank on 2007-05-13
> **SUBS0nic said:**
> Hello all, I just installed ubuntu on my laptop and for the life of me cannot get the wireless to work, i have tried to look for the driver but could only find articles by people looking for the same answer, i like to travel with my laptop so i need the wireless to work. im not sure what i'm supposed to offer in the terms of info so just ask me what you think should help and ill try to answer, this si my first linux try so forgive the newbness . also thanks in advance

Hi and welcome this thread may help you
[http://ubuntuforums.org/showthread.php?t=438903&highlight=Presario+V5000](http://ubuntuforums.org/showthread.php?t=438903&highlight=Presario+V5000)
Good luck!:)

---

### Post by SUBS0nic on 2007-05-13
whats a terminal?

---

### Post by overdrank on 2007-05-13
> **SUBS0nic said:**
> whats a terminal?

It is under application,accessories,terminal, :)

---

### Post by Bachstelze on 2007-05-13
[Where's the terminal ?](http://psychocats.net/ubuntu/terminal)

---

### Post by SUBS0nic on 2007-05-13
Ok i found the terminal (thanks guys) and it says 14e4 : 4318

---

