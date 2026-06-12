---
title: "vlc not shown"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-06-02
please help am new to linux and just tried installing vlc media player using the following commands

sudo alien vlc.rpm

sudo dpkg -i vlc.deb
sudo apt-get install vlc

now vlc shows up in synaptec package manager and in add aplications but does not show up in the applications menu under sound and music what else can i do

---

### Post by Jagot on 2006-06-02
You shouldn't mess around with .rpm's as vlc is available in the repositories.  From the commands you've written it appears that you've installed both a file for vlc you have downloaded, then also tried to install the one in the repositories.  Go to Synaptic and remove anything to do with vlc.  Then, go back to Synaptic and reinstall vlc from the repositories or run the command:

```
sudo aptitude install vlc
```

---

### Post by vidak on 2006-06-02
Maybe you couldn't find vlc in the package list because it is in the universe repository. It can be added either editing /etc/apt/sources.list (after saving it, of course) manually (with vi, emacs, kate or whatever you like), or using adept/synaptic (depending on that you are using kde or gnome). 
After editing this file, run sudo apt-get update
to update your package list then vlc should be present in that list...
Good luck!

---

### Post by Jagot on 2006-06-02
Good point.  Here's asyiu's guide to adding the repositories which may be easier for you:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

