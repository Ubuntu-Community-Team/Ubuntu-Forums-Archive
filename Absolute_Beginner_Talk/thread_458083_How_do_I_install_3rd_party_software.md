---
title: "How do I install 3rd party software?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by stevezygote on 2007-05-29
I've downloaded a "run" file. It's a tarball I believe with the run appendage. How do I install it? It's strike vega. I just wanted to install it for the experience and to have some fun. But the package manager doesn't seem to want to cooperate.

---

### Post by taurus on 2007-05-29
Applications -> Accessories -> Terminal
```
cd ~/Desktop  <-- change to directory where you download it
chmod 755 **filename.run**  <-- change permissions so you can execute to install it
./**filename.run**  <-- execute it to either install it or run it.
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by lazyart on 2007-05-29
Check the directions where you downloaded it.  Likely you will have to give it eXecute permission first:```
sudo chmod +x *filename*
```and then you can execute it.

Again, when installing 3rd party stuff their instructions are the best.

---

