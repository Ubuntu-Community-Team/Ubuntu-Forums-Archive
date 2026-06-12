---
title: "trouble installing mplayer"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-10-12
HI, I'm attempting to install mplayer as per these instructions:
[https://help.ubuntu.com/community/MPlayer/Breezy](https://help.ubuntu.com/community/MPlayer/Breezy)

when I type in the ./configure command I get a message telling me that permission deied, what is going wrong? here is the whole terminal.

kyle@ubuntu:~$ sudo apt-get install mplayer-586
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mplayer-586
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.5kB of archives.
After unpacking, 86.0kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse mplayer-586 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 [42.5kB]
Fetched 42.5kB in 0s (56.2kB/s)
Selecting previously deselected package mplayer-586.
(Reading database ... 77439 files and directories currently installed.)
Unpacking mplayer-586 (from .../mplayer-586_2%3a0.99+1.0pre7try2+cvs20060117-0ubuntu8_all.deb) ...
Setting up mplayer-586 (0.99+1.0pre7try2+cvs20060117-0ubuntu8) ...
kyle@ubuntu:~$ ~/.mplayer/config
bash: /home/kyle/.mplayer/config: Permission denied
kyle@ubuntu:~$ # Specify default video driver (see mplayer -vo help for a list).kyle@ubuntu:~$ vo=xv,sdl,x11
kyle@ubuntu:~$
kyle@ubuntu:~$ ~/.mplayer/config
bash: /home/kyle/.mplayer/config: Permission denied
kyle@ubuntu:~$

---

### Post by Perfect Storm on 2006-10-12
```
cd 
gedit /.mplayer/config
```

---

### Post by timmins on 2006-10-12
I can't get it to work, I'll just have my brother in law come over and show me everything sometime this week.
Thanks for the help anyway.

---

### Post by anaconda on 2006-10-12
> **Artificial Intelligence said:**
> ```
cd 
gedit /.mplayer/config
```
NO! it is 
gedit ~/.mplayer/config

the ~ is important without it you are trying to edit
/.mplayer/config
instead of:
/home/username/.mplayer/config
which you want to edit..
you could also go to the correct folder, and then type:
gedit config
or 
nano config

---

### Post by Perfect Storm on 2006-10-12
sorry, it's a mistype.

---

