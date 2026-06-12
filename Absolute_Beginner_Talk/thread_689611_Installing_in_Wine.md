---
title: "Installing in Wine?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by SIXAXIS on 2008-02-06
Hi again guys,

I finally managed to get my computer running properly! :) But I wanted to use some of my Windows apps without booting into Windows, so I installed Wine. Everything is okay but I don't know how to install programs that I have installed on my *real* Windows setup. I tried copying the folder from Program Files in the real Windows to the Program Files in Wine, but still nothing. I tried adding the programs to the Wine Config Compatibility list and still nothing.

Can you guys help me install a program that I had before on Windows?

---

### Post by emarkd on 2008-02-06
I haven't used Wine much and don't know about copying already installed programs, but if you have the installer, you can just launch the installer using Wine and Wine'll handle the rest:

```
$ wine setup.exe
```

---

### Post by SIXAXIS on 2008-02-06
> **emarkd said:**
> I haven't used Wine much and don't know about copying already installed programs, but if you have the installer, you can just launch the installer using Wine and Wine'll handle the rest:

```
$ wine setup.exe
```

OK, thanks. I'll just use that to run my program.

---

### Post by TMpBG on 2008-02-06
Hmm as a noob my advice may be silly...try click right mice button on some setup.exe and run with wine or what is writhed there...

---

