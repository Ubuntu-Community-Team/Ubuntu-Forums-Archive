---
title: "[SOLVED] permision denied"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-01-14
i am trying to install the win32codecs onto my pc using the guide from this website

[http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml]("http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml")

it says i have to make to 2 directories one being
```
mkdir /usr/local/lib/codecs/
```
im getting permision denied.

what am i doing wrong?

thanks
Peter

---

### Post by fiddledd on 2008-01-14
Try "sudo mkdir /usr/local/lib/codecs"

---

### Post by NilsE on 2008-01-14
Just put    sudo    in front of the command

However, there is an easier way to install it from Synaptic. Just make sure all repositories are turned on in the Software Sources gui.

---

### Post by PetePete on 2008-01-14
an easier way is to install from the repositories, then you get updates :D

you'll need to add new repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bumanie on 2008-01-14
Follow this thread, it should work.
[http://phorolinux.com/how-to-install-non-free-multimedia-codecs-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-non-free-multimedia-codecs-on-ubuntu-710-gutsy-gibbon.html)

---

### Post by pedrom169 on 2008-01-14
thanks all for the help. works now :)!

---

### Post by Dr Small on 2008-01-14
> **pedrom169 said:**
> thanks all for the help. works now :)!
Then please mark your thread as Solved, from the Thread Tools :)

Thanks,
Dr Small

---

