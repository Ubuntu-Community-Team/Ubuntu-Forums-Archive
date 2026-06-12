---
title: "help installing something on linux"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by newhen on 2006-04-02
Here is the problem, I download a game , in this case lincity, i go to synpact pakage manger, i search for lincity and get no results what am i doing wrong. 
p.s im a complete noob to linux.

---

### Post by newhen on 2006-04-02
P.S if any of you want to help me alot by talking to me via AIM chat newhen222

---

### Post by Sutekh on 2006-04-02
[QUOTE=newhen]Here is the problem, I download a game , in this case lincity, i go to synpact pakage manger, i search for lincity and get no results what am i doing wrong. 
p.s im a complete noob to linux.[/QUOTE]Synaptic works by downloading applications from the online repositories.  If you download something yourself, you will have to install it yourself.

Having said that **lincity** is in the universe repository, so with some editing you can use Synaptic to get it.

You need to first enable the universe repository. 

This will backup and edit the sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
Look for lines containing **universe** and remove the # signs in front.  Save the file (Ctrl+O) and exit (Ctrl+X).

Refresh the repositories list and then install lincity
```
sudo apt-get update
sudo apt-get install lincity
```

---

### Post by Sutekh on 2006-04-02
[QUOTE=newhen]Here is the problem, I download a game , in this case lincity, i go to synpact pakage manger, i search for lincity and get no results what am i doing wrong. 
p.s im a complete noob to linux.[/QUOTE]
Also could you supply the name of the file you downloaded and where from?

I was just checking out the Lincity website, and the version available in the universe repository is 1.13 (unstable).  The version 1.12 is the latest stable one, so perhaps you'd be better off getting that one and installing it yourself.  

If you do use the unstable 1.13 don't forget to bring up any bugs/issues in the Lincity forum.

[Lincity Forum at SourceForge.net]("http://sourceforge.net/forum/?group_id=33390")

---

