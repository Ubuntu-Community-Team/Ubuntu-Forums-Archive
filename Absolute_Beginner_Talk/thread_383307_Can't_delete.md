---
title: "Can't delete"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-13
Ok, here's the problem.  I have uninstalled 2 applications using automatix, but they are still listed in my applications menu.  How do I delete them from there ??

---

### Post by xyz on 2007-03-13
What progs are we talking about?
Also [see this]("http://ubuntuforums.org/archive/index.php/t-90797.html")

---

### Post by gettinoriginal on 2007-03-13
aMSN and gYachE

---

### Post by xyz on 2007-03-13
What are the outputs of:
```
locate aMSN
```
and
```
locate gYachE
```

---

### Post by gettinoriginal on 2007-03-13
using the page you gave me, amsn is gone, but gYachE gives me this:
E: Couldn't find package gYachE

---

### Post by xyz on 2007-03-13
When trying to 'locate', make sure gYachE is really spelled that way; see how Automatix spelled it.
If "E: Couldn't find package gYachE", then it may be that it's gone.

---

### Post by gettinoriginal on 2007-03-13
/home/gettinoriginal/.local/share/applications/gyachi.desktop

---

### Post by gettinoriginal on 2007-03-13
and now when I try to remove them with apt-get auto removal, it says:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by gettinoriginal on 2007-03-13
and yes, I already did the gksudo nautilus thing, and permission is denied

---

### Post by gettinoriginal on 2007-03-13
I got to the root files, and now the program is gone, but the title it installed on my app list is GYachE Improved, and no matter what terminal command I use, it states:
Cant find package  !! the package is gone, all I want to get rid of is the title in the apps list

---

### Post by xyz on 2007-03-13
In a terminal, you could try:

```
sudo -s
```
password
```
cd /home/gettinoriginal/.local/share/applications/
```
```
ls
```
to see what's in there.
If I understood you right, you should find 'gyachi.desktop' in there.
 so proceed to remove it.
```
rm gyachi.desktop
```
Sometimes I open 'Computer' as root and delete by hand.
I hope I understood what you meant. Let me know.

---

### Post by gettinoriginal on 2007-03-13
Thank you, you did it !!!!!!!!!!!  I really appreciate all the effort you put into a newbies problem.  Have a cup of ubuntu on me  ;)

---

### Post by xyz on 2007-03-13
> **gettinoriginal said:**
> Thank you, you did it !!!!!!!!!!!  I really appreciate all the effort you put into a newbies problem.  Have a cup of ubuntu on me  ;)

Glad I could help! Don't worry, lots of people help me here. I'm just a noob a tiny bit further down the road than you.
Hang in there and come back for help if need be! Ciao!

---

