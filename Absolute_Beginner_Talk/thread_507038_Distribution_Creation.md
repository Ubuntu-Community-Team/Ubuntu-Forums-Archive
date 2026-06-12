---
title: "Distribution Creation"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by xstevex on 2007-07-22
Hey, I would like to start creating a ubuntu based distrobution personalised for my needs, with different features, and designed with my computers in mind to save the time it takes every time i install. I also fix peoples computers as a hobby, and i am often asked for linux to be installed and would like to have a personalised distro

can anyone give me an easy enough tut. that explains it in n00b terms. Im not amazing with linux, but im comfortable with the command line and know what im doing.

---

### Post by raja on 2007-07-22
Have a look at [reconstructor]("http://reconstructor.aperantis.com/").

---

### Post by xstevex on 2007-07-23
lol. i've used that before and forgotten all about it xD

downside is the small amount of modules, but it'll do.. :D

---

### Post by 3rdalbum on 2007-07-23
Reconstructor does decompress the filesystem image from the Live CD, so if you decided to put it into /home/chris/edit:

```
sudo chroot /home/chris/edit
```

Hey presto, you've got a command-line that treats the decompressed filesystem as though it were your root. Within this command-line, you can apt-get packages and make all sorts of modifications, before using Reconstructor to put it all back together again into a CD.

---

