---
title: "How to install a tarball"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-10-09
Hey all,

I just downloaded what I presume to be a "tarball" to my desktop. How do I install this? To be exact, the file is [http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.2/f-spot-0.2.1.tar.bz2](http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.2/f-spot-0.2.1.tar.bz2)

Thank you!!

---

### Post by fatsheep on 2006-10-09
Try this:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by divague on 2006-10-09
first uncompress it

tar xvjf f-spot-0.2.1.tar.bz2

cd *name-of-the-folder*

./configure

make

sudo make install

---

### Post by Arisna on 2006-10-09
F-Spot is available in the Ubuntu's universe repository, too.  Installing from there would be easier than from source.  Do you have a special need to install from source?

---

### Post by aysiu on 2006-10-10
Arisna has a good point.

As long as you enable extra repositories...
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

... you should be able to install it with this command: ```
sudo aptitude update && sudo aptitude install f-spot
``` No need for the .tar.gz file at all

---

### Post by halitech on 2006-10-10
but where is the fun of installing it using synaptic or aptitude? come on guys, command line is what it's all about :D

---

### Post by lemonsCC on 2006-10-10
**FYI**F-spot DOES NOT save its tags and date data to the photo it creates a .db source that it reads from.  This can be a big headache when you want to switch apps, etc.  digikam is the photomanager I will be trying soon, as it DOES write tag and albums data to the photo.

---

### Post by Jordan Meeter on 2006-10-10
> **Arisna said:**
> F-Spot is available in the Ubuntu's universe repository, too.  Installing from there would be easier than from source.  Do you have a special need to install from source?
Ehh, no. I was just on the site and downloaded the file from the site. Didn't really think of Synaptic or anything.

---

