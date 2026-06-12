---
title: "mplayer install"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-17
trying to install mplayer(need this for sirius online) following instructions fromm here [http://eli.criffield.net/sipie/sipie_README](http://eli.criffield.net/sipie/sipie_README) but not to sure about this in the instructions 

To run just copy sipie somewhere in your path 
cp sipie ~/bin/sipie

so how do i do that,thanks :mrgreen:

---

### Post by mcduck on 2006-12-17
those are pretty strange instructions for such a simple task..

[How to install *ANYTHING* in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by taurus on 2006-12-17
Applications -> Accessories -> Terminal
```
cp sipie ~/bin/sipie
```
(assuming that you are in the same directory where sipie is located!!!  Also, ~/bin has to be in your path or else you have to type the whole thing out, **~/bin/sipie** instead of just **sipie**, if you want to run it...)

---

### Post by wilderness wanderer on 2006-12-17
You can put it in /usr/bin which is automatically in every user's path.  Also make sure the file is set to be executable in the permissions.  Assuming you are in the directory containing the file, 

```
sudo chmod a+x sipie
sudo cp sipie /usr/bin
```

Then just type sipie and it should run (assuming you have Beautiful Soup and Python installed.)  See [this]("http://ubuntuforums.org/showthread.php?t=284893&highlight=sipie") thread.

---

### Post by elicriffield on 2007-01-05
> **wilderness wanderer said:**
> You can put it in /usr/bin which is automatically in every user's path.  Also make sure the file is set to be executable in the permissions.  Assuming you are in the directory containing the file, 

```
sudo chmod a+x sipie
sudo cp sipie /usr/bin
```

Then just type sipie and it should run (assuming you have Beautiful Soup and Python installed.)  See [this]("http://ubuntuforums.org/showthread.php?t=284893&highlight=sipie") thread.

Much better idea, updated the README

---

