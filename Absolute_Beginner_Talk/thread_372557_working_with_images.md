---
title: "working with images"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-02-28
i need a good simple tool for managing images. gwenview is fine but i can't find the way to cut images for example :D ....

---

### Post by taurus on 2007-02-28
Maybe Gimp is what you are looking for!

---

### Post by mendingo84 on 2007-02-28
maybe, but how do i install it? can't find it in the repos

---

### Post by taurus on 2007-02-28
Gimp should already be on your system.  Look in Applications -> Images.  Or 

Applications -> Accessories -> Terminal
```
gimp
```

---

### Post by mendingo84 on 2007-02-28
don't think so... i'm a KDE user...and "dpkg -l | grep gimp" provides nothing

---

### Post by taurus on 2007-02-28
Yip.  Forgot to look at your profile.

What happens if you run these?

```
sudo aptitude update
sudo aptitude install gimp
```

---

### Post by ieee488 on 2007-02-28
Picasa !!!!
from Google has a Linux version

---

### Post by mendingo84 on 2007-02-28
told you it's not in the repos :)
 
> 
sudo aptitude install gimp
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for gimp
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


funny thing (not relevant though) is i'm also having some trouble with the backports...can't connect to them...

---

### Post by taurus on 2007-02-28
Post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by mahiyar on 2007-02-28
I second the opinion of ieee488, picassa is a great program, its deb file is available for download from [http://picasa.google.com/linux/](http://picasa.google.com/linux/)  afaik it is not in the repositories.

---

