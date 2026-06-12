---
title: "In Add/Remove Programs..."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Shadowstorm on 2007-06-01
Hello. I am trying to find out why Ubuntu is giving me this error message when trying to download/install k3b and AmoraK:

[IMG]http://img.photobucket.com/albums/v628/Agentstorm/Screenshot.png[/IMG]

Would anyone be able to help me out?

---

### Post by jonward0690 on 2007-06-01
Well can you run sudo commands

---

### Post by taurus on 2007-06-01
Try to run it from a terminal to see exactly what the problem is.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by Shadowstorm on 2007-06-12
It doesn't work =/.

I went into Terminal and entered "sudo update", "sudo aptitude update", and nothing happens. Just asks me for my password and that's it.

I really want to learn how to use this, but my experience has been relatively frustrating.

---

### Post by abn91c on 2007-06-12
those are kde(kubuntu) programs, you need to try in a root terminal: sudo apt-get check,
it may tell you to try certain command, if it does to as it tells you. Also try typing apt-get update followed by apt-get ugrade

---

### Post by init1 on 2007-06-12
I think it may be a sudoers issue. Try a ```
sudo su
``` If it doesn't work, you may need a new sudoers file.

---

