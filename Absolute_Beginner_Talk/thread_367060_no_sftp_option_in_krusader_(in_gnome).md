---
title: "no sftp option in krusader (in gnome)"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2007-02-21
I'm trying to find a nice gui for sftp. 

I heard about krusader but when I try to "make a new net connection", the only protocol it shows me is "ftp". I'm using gnome. do you know why this might be?

I tried searching but, search keywords suck..

thanks :)

---

### Post by mahy on 2007-02-21
Yeah, this happened to me as well. Not sure what causes it. It DID work in Breezy. Now i have to use gFTP. :(

---

### Post by jpeddicord on 2007-02-21
Try gFTP. In the program, this is listed as SSH in the settings. It may take some time getting used to gFTP's quirks, but in the end it is pretty easy to use.

Also, if you are on edgy, you can use Gedit with GNOME's SSH support to directly save files on the server instead of having to reupload them every time. :)

---

### Post by towsonu2003 on 2007-02-21
thanks. I had some confusion about gftp (the protocols sftp and ftps confused me) bu this thread helped me: [http://ubuntuforums.org/showthread.php?p=2191042#post2191042](http://ubuntuforums.org/showthread.php?p=2191042#post2191042)

I'll go with gftp but open a bug report for krusader (if there is none yet)

edit: bug report just opened here- [https://launchpad.net/ubuntu/+source/krusader/+bug/86927](https://launchpad.net/ubuntu/+source/krusader/+bug/86927)

---

### Post by Copter on 2007-07-11
The solution is found by checking the launchpad link that towsonu2003 has posted. In my case (Xubuntu 6.10) it did the trick: install **kdebase-kio-plugins** (approx 1MB) using Synaptic or
```

sudo apt-get install kdebase-kio-plugins

```Thanks! [SOLVED]

copter :]

---

