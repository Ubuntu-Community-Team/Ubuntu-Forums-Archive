---
title: "Installing .rpm file [Resolved]"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-05-06
I'm trying to install pdfedit from an .rpm file which I have downloaded to the Desktop. I have alien installed. I'm using Ubuntu 6.10.
I entered: cd Desktop
sudo alien -i
pdfedit-0.3.1-1.i386.rpm
The third entry produces: Command not Found.
What am I doing wrong?
Thanks

---

### Post by taurus on 2007-05-06
```
alien pdfedit-0.3.1-1.i386.rpm
sudo dpkg -i pdfedit-0.3.1-1.i386.deb
```

---

### Post by aysiu on 2007-05-06
These two links should help you:
[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Stunt Double on 2007-05-06
Problem solved. 
Thanks for the help Taurus and Aysiu.

---

