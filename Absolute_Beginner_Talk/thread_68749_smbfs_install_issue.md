---
title: "smbfs install issue"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by jjtoymachine on 2005-09-24
Hi there,

im trying to install samba so i can network with my windows xp bowes, i have done the apt-get install samba and that installs fine but when i do apt-get install smbfs i get a dependant on other files error message. and it say please add all repositories but the thing is i have.

Any ideas?

---

### Post by tonym on 2005-09-24
For people to help you need to publish the error messages and the contents of your /etc/apt/sources.list file.

---

### Post by jjtoymachine on 2005-09-24
[QUOTE=tonym]For people to help you need to publish the error messages and the contents of your /etc/apt/sources.list file.[/QUOTE]

these are my sources:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


The error message i get is:
[B]smbfs:
  Depends: samba-common (=3.0.14a-3ubuntu3~5.04ubp1) but 3.0.10-1ubuntu3 is to be installed[/B]

Thanks for reply

---

### Post by Abild on 2005-09-24
Try to disable the backports repositories by putting # in front of the two last lines in your sources.list file.
Then run 
```
sudo apt-get update
sudo apt-get install smbfs
```

---

### Post by snowjunkie on 2005-09-24
I was having the same problem and this worked for me!  Thanks!  Should I leave backports commented out, or should I enable them again?

---

