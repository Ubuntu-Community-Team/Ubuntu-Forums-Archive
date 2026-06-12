---
title: "error: dependency is not satisfiable"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by webdreamer on 2007-03-09
I've posted earlier a thread on how to get the header files in C, and I was told to get libc-6-dev, which I did, and seems to have exactly what I need. The problem is I can't install it using the package installer, because I've the following error: "dependency is not satisfiable". I don't understand why this comes up or what it means. Should I get another libc-6 package? Which one? Where should I go to get it? By the way, I can't connect my laptop to the internet (or at least I'd rather not do it), so please come with solutions that don't involve it.

---

### Post by invalid on 2007-03-09
Please post the exact output of what you typed to install the package. It usually contains more information as to the dependency issues.

---

### Post by webdreamer on 2007-03-09
I used the package installer and that's all I came up with, the only thing I see on the screen. I'm new to ubuntu and I don't know wherer should I look for more information. Can you tell me?

---

### Post by invalid on 2007-03-09
```
beau@willow:~$ aptitude show libc6-dev
Depends: libc6, linux-libc-dev
```
I would attempt to install these two packages, and then try installing libc6-dev again.

---

### Post by webdreamer on 2007-03-09
Ok, I think I see what you mean, because it says dependency is not satisfiable: libc6, which, I suppose, it means libc6 it's not installed. However I've tried to installed a version of it and the installer said a newer version was already instaled. I don't understand why the dependency error then. Anyway I'm now looking for the same version of lic6 as I have of libc6-dev.
And thanks for helping me out.

---

### Post by webdreamer on 2007-03-09
It's not working. Libc-6 is already installed and it's a more recent version than 2.3.6 - or so the installer says. Is there any code to see what version of libc-6 I do have already installed? What do I do next?

---

### Post by invalid on 2007-03-09
> **webdreamer said:**
> Is there any code to see what version of libc-6 I do have already installed?

```
dpkg -l | grep libc6
```

---

### Post by webdreamer on 2007-03-09
Ok, it was a version problem after all... Solved now, everything is working fine, thanks!

---

