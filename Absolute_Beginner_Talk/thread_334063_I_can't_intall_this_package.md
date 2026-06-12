---
title: "I can't intall this package"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-01-08
Hello,

There are two packages I can't intall:
x-window-system-dev and libpng-dev
By typing > sudo apt-get install libpng-dev
I get this:
> Reading package lists... Done
Building dependency tree... Done
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.8rel-5ubuntu0.1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate

Help!

---

### Post by taurus on 2007-01-08
```
sudo aptitude update
sudo aptitude install libpng12-dev
```

---

### Post by linux-beginner on 2007-01-08
Thanks, it's solved. but this:
> sudo aptitude install x-window-system-dev
results this:
> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "x-window-system-dev"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
:confused:

---

### Post by taurus on 2007-01-08
```
sudo aptitude install xorg-dev
```

---

### Post by linux-beginner on 2007-01-08
This code worked well:
```
sudo aptitude install xorg-dev
```
but after that i tried this:
```
 sudo aptitude install x-window-system-dev
```
and then I got this:
> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "x-window-system-dev"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by taurus on 2007-01-08
I don't think there is such a package, x-window-system-dev.  Since Ubuntu (and most of other Linux distros) are using Xorg, you just install the xorg-dev package then.  Now, what are you trying to build from source?

---

### Post by linux-beginner on 2007-01-08
I follow this instructions:
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)
to install mplayer!

---

### Post by taurus on 2007-01-08
Any reason why you need to build mplayer since you can install it with automatix and it's in the repos?

---

### Post by linux-beginner on 2007-01-08
Actually I want to learn more about Ubuntu and commends :p 
I have to go shopping.
I'll come back over 2 hours.
Thanks for information!

---

