---
title: "Installing alien"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Seisen on 2008-03-28
If you have synaptic or add/remove programs open and you try to apt-get something it will give you that error.

---

### Post by DBrocks on 2008-03-28
Run
```
sudo apt-get --fix-missing
```
then
```
sudo apt-get update
```

Then try running
```
sudo apt-get install alien
```

---

### Post by philinux on 2008-03-28
Make sure synaptic is not open at the same time.

---

### Post by TeoBigusGeekus on 2008-03-28
Rpm files are installation files used by other Linux distributions (Fedora Core). Ubuntu uses .deb files. Why don't you download the limewire .deb file?
[http://www9.limewire.com/download/LimeWireLinux.deb]("http://www9.limewire.com/download/LimeWireLinux.deb")
Save it somewhere and the double click it. Limewire will be automatically installed...

---

### Post by DBrocks on 2008-03-28
And try this link:[ http://ubuntuforums.org/showthread.php?t=499211]("http://ubuntuforums.org/showthread.php?t=499211")

---

### Post by mrsudo on 2008-03-28
close anything related to synaptic, such as synaptic itself, add/remove, terminal running apt-get, or update

---

