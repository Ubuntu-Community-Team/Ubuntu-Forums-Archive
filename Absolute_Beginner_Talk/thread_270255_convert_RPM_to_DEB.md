---
title: "convert RPM to DEB?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-10-02
How is it again that I convert RPMs to DEB packages to install?
(for example,... the rpm for LimeWire)

---

### Post by sonny on 2006-10-02
First you'll have to install the alien package, just do:
```
sudo apt-get install alien
```

Then in order to convert a rpm to deb you just have to type:
```
sudo alien -d your_package.rpm
```

That's all, then you just install it with double click.

---

### Post by baylorbear on 2006-10-02
Perfect!

Thank you! :)

---

