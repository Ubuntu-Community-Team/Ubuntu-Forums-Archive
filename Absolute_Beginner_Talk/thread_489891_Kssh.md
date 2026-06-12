---
title: "Kssh"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by will12 on 2007-07-01
I am wondering how to get an SSH program similair to PuTTY.

---

### Post by Marshall2day on 2007-07-02
I believe there is a linux port of PuTTY. I never tried it though, so I don't know if it's on par with the windows version.

---

### Post by vexorian on 2007-07-02
You don't need it, at all.

On konsole/terminal type : 

```

ssh --help

```

or
```

man ssh

```
if you need more details.

the ssh command will connect your terminal to a ssh server and it is exactly like putty.

---

### Post by Seisen on 2007-07-02
Putty is in the repositories so you can download it using apt-get or synaptic. Just make sure that you have the universe repositories enabled.

---

### Post by eternalsword on 2007-07-02
yes, putty is available in the repositories.  it won't look very pretty as it's gtk1, but it's on par with the windows version in terms of functionality.

---

