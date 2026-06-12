---
title: "How to Install CrossPacker-0.1-PR1?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by alexandros81 on 2007-07-07
I extracted the contents of the tar.gz file
The new folder created contains the build_package.py script.
I found the following information on [http://kevino.theolliviers.com/crosspacker/download.html](http://kevino.theolliviers.com/crosspacker/download.html) 
"
You need Python 2.3 installed to run the build_package.py script, and you'll need to install the latest versions of NSIS and/or InnoSetup to build packages for those systems. "

How do i proceed?

---

### Post by Ozeuss on 2007-07-07
I don't know about this specific software, but from the message you posted, you might try to install python and nsis packages.
actually, python is supposed to be already installed on your system (not 2.3, but a newer version- 2.5)
```
sudo apt-get install python nsis
```

---

