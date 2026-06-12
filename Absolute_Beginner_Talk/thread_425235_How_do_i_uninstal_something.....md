---
title: "How do i uninstal something...."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-04-27
I accidentally installed something using the terminal...
Anybody knows which command to give to uninstall it...?
Thanx guys...:guitar:

---

### Post by compmodder26 on 2007-04-27
What command did you do give to install it?  Something like "apt-get install" or "aptitude install"?  Or was it something like "./configure && make && sudo make install"?

---

### Post by BHelts on 2007-04-27
```

sudo apt-get remove [package]

```
where package is what you installed without the brackets

---

### Post by tyboon on 2007-04-27
it was this command..."apt-get install"
```
What command did you do give to install it? Something like "apt-get install" or "aptitude install"? Or was it something like "./configure && make && sudo make install"?
```
So whats the deal now...?

---

### Post by Cypher on 2007-04-27
Do
```

sudo apt-get autoremove <pkg>

```
and it will remove that package and any unused things it installed..

---

