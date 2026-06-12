---
title: "Problem with installing xvkbd and xvindkeys"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-11-29
Hello, I was working with a "HOWTO"
[http://www.ubuntuforums.org/archive/index.php/t-125752.html](http://www.ubuntuforums.org/archive/index.php/t-125752.html)

and they worte :
First install xvkbd and xvindkeys.
```
sudo apt-get install xvkbd xbindkeys
```

but when i wrote that the output was :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xvkbd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvkbd has no installation candidate
```
How i solve it ?

---

### Post by Ecthelion on 2006-11-29
> This may mean that the package is missing, has been obsoleted, or
is only available from another source

I guess you don't have the universe repos...
Once you added the universe repos, reload your packages list and try again

---

### Post by tiptip on 2006-11-29
> **Ecthelion said:**
> I guess you don't have the universe repos...
Once you added the universe repos, reload your packages list and try again
How i do that ? :D

---

### Post by kerry_s on 2006-11-29
Use synaptic, it's there i use xvkbd all the time, but you don't need xbindkeys for xvkbd.
Also if your using gnome, you should have gok installed already. Gok is the gnome on-screen keyboard, look under accessibility.

---

### Post by Ecthelion on 2006-11-29
> **tiptip said:**
> How i do that ? :D

Go to System > Administration > software sources
Just check the universe box :-)

---

