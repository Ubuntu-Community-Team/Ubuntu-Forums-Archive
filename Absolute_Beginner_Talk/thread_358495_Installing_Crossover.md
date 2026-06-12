---
title: "Installing Crossover"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-10
I get this message when I try to install crossover is there a way around it?

[IMG]http://i14.tinypic.com/343gfia.png[/IMG]

Thanks](*,)

---

### Post by Griff on 2007-02-10
lol.  Sorry, but you might want to submit another pic.  I don't see what this game screenshot is supposed to mean. :lolflag:

---

### Post by Repent on 2007-02-10
lol...Sorry

---

### Post by taurus on 2007-02-10
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 install-crossover-standard-demo-6.0.0(2).sh
./install-crossover-standard-demo-6.0.0(2).sh
```

---

### Post by Repent on 2007-02-10
This is what I get,

joe203@joe203-desktop:~$ cd ~/Desktop
joe203@joe203-desktop:~/Desktop$ chmod 755 install-crossover-standard-demo-6.0.0(2).sh
bash: syntax error near unexpected token `('
joe203@joe203-desktop:~/Desktop$ ./install-crossover-standard-demo-6.0.0(2).sh


Thanks for your help.

---

### Post by taurus on 2007-02-10
```
chmod 755 "install-crossover-standard-demo-6.0.0(2).sh"
./"install-crossover-standard-demo-6.0.0(2).sh"
```

---

### Post by Repent on 2007-02-11
That worked thank you.

---

