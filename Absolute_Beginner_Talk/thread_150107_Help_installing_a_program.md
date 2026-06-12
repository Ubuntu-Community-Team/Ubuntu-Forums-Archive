---
title: "Help installing a program"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by scratched on 2006-03-25
I'm literally at day one with linux, and I'm trying to set up widescreen support (1280x800) using [this guide]("http://users.skynet.be/thomasvst/linux-on-laptop/#wide") I found after searching the forums. I was able to untar the download, but when I type in "make", I get this error:
```
:~/915resolution-0.5.2$ make
bash: make: command not found

```

I read the ubuntu wiki about compiling software and I read the [readme]("http://www.geocities.com/stomljen/readme.html") for the file I untarred and I don't need any extra packages as far as I can tell. What do I need to do to get this to work?

---

### Post by halitech on 2006-03-25
[QUOTE=scratched]I'm literally at day one with linux, and I'm trying to set up widescreen support (1280x800) using [this guide]("http://users.skynet.be/thomasvst/linux-on-laptop/#wide") I found after searching the forums. I was able to untar the download, but when I type in "make", I get this error:
```
:~/915resolution-0.5.2$ make
bash: make: command not found

```

I read the ubuntu wiki about compiling software and I read the [readme]("http://www.geocities.com/stomljen/readme.html") for the file I untarred and I don't need any extra packages as far as I can tell. What do I need to do to get this to work?[/QUOTE]


I would almost have to say make didn't get installed with everything else but you should be able to install it from System-> Administration-> Synaptic and do a search for make

---

### Post by KansasJoe on 2006-03-25
sudo apt-get install build-essential

---

### Post by halitech on 2006-03-25
KansasJoe, that looks even easier and along my lines of wanting to try everything with the command line. I've even learned how to convert movies for burning on dvd with the cli.

---

### Post by halitech on 2006-03-25
KansasJoe, that looks even easier and along my lines of wanting to try everything with the command line. I've even learned how to convert movies for burning on dvd with the cli.

---

### Post by scratched on 2006-03-25
That command line worked. Thanks.

---

