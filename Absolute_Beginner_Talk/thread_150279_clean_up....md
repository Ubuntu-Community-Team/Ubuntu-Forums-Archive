---
title: "clean up..."
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-25
So i have a 60 gig hard drive with a ubuntu install

13gigs of it are used up by my music and my pictures.  I only have 11gigs free, so that means 36 gigs are being used by ubuntu?? is there something wrong here...

how can i clean up my system, or atleast figure out what the hell is takin up so much space.

---

### Post by trent dillman on 2006-03-25
open a terminal and try
```
du -h
```

---

### Post by obey43 on 2006-03-25
didnt really do much for me... 

it doesn't show hidden files...

is there a way to remove all the installation files from synaptic, because thats my guess what is taking up so much...

---

### Post by xXx 0wn3d xXx on 2006-03-25
Under Synaptic and then Under properties make it delete the packages. Then open Update Manager and then go under preferences and then settings and set it to auto clean and delete packages.

---

### Post by trent dillman on 2006-03-25
My guess is there's 2 partitions? Or maybe you've got a ton of stuff installed, including a couple kernels?

---

### Post by Mustard on 2006-03-25
If you would like a graphical representation of the way your hard drive is being used try installing the filelight package.

```
sudo apt-get install filelight
```

Its available from the universe repository

```
Package: filelight
Priority: optional
Section: universe/kde
Installed-Size: 856
Maintainer: James Troup <james@nocrew.org>
Architecture: i386
Version: 0.99beta6-0ubuntu3
Depends: kdelibs4c2 (>= 4:3.4.2), libc6 (>= 2.3.4-1), libqt3-mt (>= 3:3.3.4), libstdc++6 (>= 4.0.1)
Filename: pool/universe/f/filelight/filelight_0.99beta6-0ubuntu3_i386.deb
Size: 327230
MD5sum: 297370f977d9cf5652f17e8d25868323
Description: show where your diskspace is being used
 Allows you to exactly understand exactly your disk usage by
 graphically representating your filesystem as a set of concentric
 segmented-rings.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by bluevoodoo1 on 2006-03-25
Could also try...

```
sudo apt-get clean
```

and

```
sudo apt-get autoclean
```

read...
```
man apt-get
``` 

for the details.

(This is similiar to what masterchief suggests)

---

