---
title: "How do i set up network sharing ?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-27
Hi guys,

first of all.thank you for all the help. Wonder if you can show me how to set this laptop for sharing so i can transfer some of my music files from my PC be i UBUNTU the sucker :)

---

### Post by patrick295767 on 2006-05-27
```
apt-get -f -y install gnome-panel
```
 
as user: 
gnome-panel &
  
You  can see that there is in the bar the possibility of sharing folders :-)
Share
  
Have a look there or 
  
  = More complete sharing
to share via nfs (between linux boxes) you can use exports configuration: 
[http://www.ubuntuforums.org/showthread.php?t=142526&highlight=slow+nfs](http://www.ubuntuforums.org/showthread.php?t=142526&highlight=slow+nfs)

---

### Post by edwardzafra on 2006-05-27
vlad@Appoloin:~$ apt-get -f -y install gnome-panel
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list diriectory
vlad@Appoloin:~

why is this?

---

### Post by deja2004 on 2006-05-27
You must be root. Try this:
```
sudo apt-get -f -y install gnome-panel
```

---

