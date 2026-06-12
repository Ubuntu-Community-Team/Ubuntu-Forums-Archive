---
title: "Tool for analyzing Filesystem"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by maqua on 2006-01-13
Hi

i installed ubuntu 2 month ago and now 99%  of my 40gb notebook hd are used and i can't really explain why.

So i am after a tool that analyses the filesystem and shows you the biggest files  or folders. 

Something like that...

Thank you
maqua

---

### Post by aysiu on 2006-01-13
How about this one? Alt-F2. Then, ```
gnome-search-tool
```

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=maqua]Hi

i installed ubuntu 2 month ago and now 99%  of my 40gb notebook hd are used and i can't really explain why.

So i am after a tool that analyses the filesystem and shows you the biggest files  or folders. 

Something like that...

Thank you
maqua[/quote] 

Cant answer for sure, but try this.

On the taskbar click SYSTEM > ADMINISTRATION > SYMAPTIC

give your password

When it opens

SETTINGS > PREFERENCES > FILES (tab) > and check Delete downloded files ffter Install.

Click APPLY

See if that helps.

---

### Post by SickTwist on 2006-01-13
This command will list the 20 largest files in /home:

sudo du -a /home | sort -n | tail -20

---

### Post by ubuntu_demon on 2006-01-13
or to see your disk space distribution in a graphical way use :
$sudo apt-get install xdiskusage
$xdiskusage

---

### Post by Lambert on 2006-01-13
Check your logs directory as that can get pretty big

```
ls -lhS /var/log | less
``` 
This will show the logs in decending file size order.

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=ubuntu_demon]or to see your disk space distribution in a graphical way use :
$sudo apt-get install xdiskusage
$xdiskusage[/quote]

Thank you

Always finding new and better ways of doing things.

Thanks sicktwist for the terminal command too.

---

