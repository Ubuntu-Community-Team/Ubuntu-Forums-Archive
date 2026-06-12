---
title: "Missing memory?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by nosushi4you on 2008-02-09
Today I did my first "real" install of Ubuntu. Everything went fine. I checked my hard drive, and it says that I only have 24.8GB left. I have nothing on my computer except for 2GB of music, and my partition is ~35GB. I checked my folders for what could be taking up so much space, and my usr folder claims to have 10.7GB worth of files in it. This seems a bit odd to me, but maybe it's supposed to be like that. Is there any was I can clear up space?

---

### Post by nosushi4you on 2008-02-09
Also, I used the sudo apt-get autoclean thing, and it didn't clear up any space.

---

### Post by matthodge on 2008-02-09
I wouldn't just go round deleting things, but there is a disk tool which can give you a visual representation of where the hard drive space is being used.

In terminal type : 
[LIST]baobab
[/LIST]

When its open goto the "Analyzer" tab and choose "Analyze Filesystem". It will take a few seconds then you will get a list of main folders on your system and their sizes. Click on this folder and a graph will be shown on the right. The large segments are the larger files on your pc.

Maybe you have some hidden data you forgot about somewhere?

---

### Post by DDuong on 2008-02-09
Hello,

See if there is anything in your /home/user/.trash folder?  Maybe there is something left over in there?

---

### Post by jan quark on 2008-02-09
or just type into the terminal to display free and used space

```
df -h
```

I like it short

---

