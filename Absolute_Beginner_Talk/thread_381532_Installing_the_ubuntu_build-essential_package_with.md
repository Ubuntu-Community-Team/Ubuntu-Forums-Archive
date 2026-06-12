---
title: "Installing the ubuntu build-essential package without internet?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Alecks on 2007-03-11
I have Wireless Internet, so when I am on Ubuntu there is no way for me to connect to the internet to install the build-essential package. So I was wondering how I would go about installing that without being on ubuntu? 

Can I download the package on Windows in an archive and then put it on Ubuntu...?

Thanks in advanced.

---

### Post by taurus on 2007-03-11
That package, build-essential, is on the install CD.  Insert the CD into a drive and at the prompt, type

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Alecks on 2007-03-11
Thanks!

---

