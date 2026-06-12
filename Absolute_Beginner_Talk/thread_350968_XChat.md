---
title: "XChat"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-01
I have installed ubuntu for the first time, now I want to install XChat but I dont know what file I should download. This is the address: [http://www.xchat.org/download/](http://www.xchat.org/download/) . I have read about the installation: [http://www.xchat.org/compiling/](http://www.xchat.org/compiling/) but it dont say what file I should download.
Can someone help me to say which file to download.
Thanks in advance.

---

### Post by taurus on 2007-02-01
I thought xchat is in the repos.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install xchat
```

Otherwise, scroll down and you will see a link for Ubuntu/Debian package.  That's the one you want to download.  Then, install it with

```
cd ~/Desktop
sudo dpkg -i *.deb
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Paerez on 2007-02-01
Inspiron: Contrary to the method of installing software in windows, most ubuntu software is installed by using ubuntu's package management system. If you go to System->Administration->Synaptic Package Manager, you will find a tool that allows you to search for and install tons of of stuff.

If you can't find files there, then the next best thing is to go online and find a .DEB file (kind of like how you would find an .EXE for a windows program). Then you can just save it to your desktop and double click it.

---

