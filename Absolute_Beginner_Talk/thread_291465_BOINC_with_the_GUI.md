---
title: "BOINC with the GUI ?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-11-02
** should be "BOINC **without** the GUI?" -- doh! **

Hi,

I have a Ubuntu LAMP server; thought I could give it something to do when it wasn't busy (which is most of the time).

Wanted to install BOINC (specifically so I could do that BBC Climate Prediction thing) ... 

Anyhow: is there a non-GUI version of BOINC I can run on my LAMP server in the background?  I searched around but couldn't find anything.

Thanks,
Damon

---

### Post by Kateikyoushi on 2006-11-02
Yes you can do it, was one of the first things I did when I set up ubuntu.
I can't find the steps how I did it but the gui is just a skin for the console client.

This should install the client.
```
sudo aptitude install boinc-client
```

---

### Post by thornomad on 2006-11-02
All right, I will get the boinc-client package an install and see if I can run it from the command line ... thanks!

D

---

### Post by thornomad on 2006-11-02
This link helped me:

[http://www.ubuntuforums.org/showthread.php?t=274385&highlight=boinc](http://www.ubuntuforums.org/showthread.php?t=274385&highlight=boinc)

Basically, install the client on the server (no GUI) and then change some settings and access the server client remotely via a GUI-ed machine.

Works fine.  Am doing stuff now.  Neat.

D

---

