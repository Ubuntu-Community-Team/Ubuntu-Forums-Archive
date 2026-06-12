---
title: "Terminal Question."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-07-05
Hi all
Just want to know how to show system detail, temperature and few other things in Terminal.. plz tell other tricks too if u know :)

Regards

---

### Post by supersonicdarky on 2007-07-05
battery % (if exists) and temp
```
acpi -t
```

---

### Post by Dark Star on 2007-07-06
And abt System specs and all that ;)

---

### Post by Dark Star on 2007-07-06
> **Dark Star said:**
> And abt System specs and all that ;)
Some 1 tell plz :p

---

### Post by overdrank on 2007-07-06
> **Dark Star said:**
> Some 1 tell plz :p

Oh Ok about system specs  
```
lspci
```
and here is a couple of  links may help
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
Hope this helps good luck!

---

### Post by p_quarles on 2007-07-06
Do check out overdrank's links. In the meantime, you might also find these useful:

"df -h" gives you the amount of free space on your hard disk
"lsusb" tells you what's on your USB ports
"ps aux" gives you all running processes.

Have fun.

---

### Post by RomeReactor on 2007-07-06
Hi. You can also use **top**, which is like the system monitor:
```
top
```
or install **htop**:
```
sudo apt-get install htop
```
and after it finishes installation:
```
htop
```
As for system specs, I find **lshw** very informative:
```
sudo lshw
```

---

