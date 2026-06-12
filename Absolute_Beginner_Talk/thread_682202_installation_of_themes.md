---
title: "installation of themes"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2008-01-29
how do i install themes and application in general that are not .deb extension i  will be grateful if i get a quick reply on that thank you

---

### Post by benfindlay on 2008-01-29
To install the themes, just download them to your desktop, or other location, launch the themes program and drag and drop the themes you've downloaded into the themes window. It will install automatically for you!

Hope this helps

---

### Post by aysiu on 2008-01-29
Read this:
[How to install anything in Ubuntu](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by benfindlay on 2008-01-29
With regards to installing files that are not debs; if they're tar.gz files, they first need to be extracted before installation. The following commands may help you here:

```
sudo tar -xfvz filename.tar.gz
cd filename
./configure
make
sudo make install
```

Hope this helps

---

### Post by nnamdi on 2008-01-29
thank you so much for your help wil read up the manual

---

