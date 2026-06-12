---
title: "system crash"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by harry756 on 2007-03-17
I have tried to install webmin from a corrupted .deb file...The system stalled... dpkg --configure -a  can not correct the error...any ideas?

---

### Post by Kateikyoushi on 2007-03-17
Try these in terminal.
```
sudo apt-get clean
sudo apt-get check
```

---

### Post by harry756 on 2007-03-17
I still get the message 'The package needs to be reinstalled, but I cant't find the archivw for it'...  The Synaptic Manager does not show anything any more...

---

### Post by harry756 on 2007-03-17
the exact error in the synaptic manager is    E:internal error opening cache(1).Please report

---

### Post by Kateikyoushi on 2007-03-17
Then try to remove.

```
sudo apt-get remove webmin
```

---

### Post by harry756 on 2007-03-17
nothing seems to be working.. The system asks for reinstallation before removal and stalls there..
the command sudo dpkg -r webmin -a  reports that the package is in a very bad inconsistent state and reinstall it before removing it... Why is it that   sudo apt-get clean wont work?

---

### Post by Kateikyoushi on 2007-03-17
Then get the package again and try this.

```
sudo dpkg -i packagename.deb
```

---

### Post by harry756 on 2007-03-17
that seems to work... thanks....

---

### Post by Kateikyoushi on 2007-03-17
Good to know thanks for the feedback.

---

