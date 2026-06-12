---
title: "Uncompressing"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Serenteit on 2007-12-21
How do I uncompress an archive? I am installing a web cam and the directions tell me to "uncompress the archive /usr/src/qc-usb-modules.tar.gz".

---

### Post by taurus on 2007-12-21
Applications -> Accessories -> Terminal
```
sudo tar xvzf /usr/src/qc-usb-modules.tar.gz
```

---

### Post by Serenteit on 2007-12-21
Thank you, but now it tells me to execute:
/usr/src/modules/qc-usb-source/quickcam.sh

However, it says no such file or directory. Sorry I'm new at Linux.

---

### Post by taurus on 2007-12-21
What's the output of this command?

```
ls -la /usr/src/modules
```

---

### Post by Serenteit on 2007-12-21
I don't think it give me one. The whole directions are

USB ID 046d:0850 Make sure the build-essential package and the correct linux-headers package are installed. Install the package qc-usb-source, uncompress the archive /usr/src/qc-usb-modules.tar.gz and execute /usr/src/modules/qc-usb-source/quickcam.sh

---

### Post by taurus on 2007-12-21
So, there is no /usr/src/modules at all!

What's the output of this command then?

```
tar tvzf /usr/src/qc-usb-modules.tar.gz
```

---

### Post by Serenteit on 2007-12-21
It installs the cam?

---

### Post by nick_h on 2007-12-21
Did you change directory to /usr/src before extracting ther archive.  If not you probably extracted it to your home directory.

---

### Post by Serenteit on 2007-12-21
No, how do I fix it? X_X I feel like such an idiot.

---

### Post by nick_h on 2007-12-21
The easiest way would be to extract it again.
```
cd /usr/src
sudo tar xvzf qc-usb-modules.tar.gz
```
Then you probably have a folder called modules in your home directory which you can delete.

---

### Post by mellowd on 2007-12-21
```
./usr/src/modules/qc-usb-source/quickcam.sh
```

or

```
cd /usr/src/modules/qc-usb-source
./quickcam.sh
```

---

