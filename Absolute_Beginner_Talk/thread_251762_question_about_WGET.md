---
title: "question about WGET"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
hello, i am wondering where do the files save once you downloaded them via terminal using WGET, and also

how do you download this script to your hardware and make it work?

[http://ting.homeunix.org/cvs_wine/GetCVSWineX](http://ting.homeunix.org/cvs_wine/GetCVSWineX)

---

### Post by x64Jimbo on 2006-09-05
wget downloads the file to whatever directory you are in when you run wget. 
type this:
```
cd ~
wget http://ting.homeunix.org/cvs_wine/GetCVSWineX
chmod a+x GetCVSWineX
sudo ./GetCVSWineX

```

---

