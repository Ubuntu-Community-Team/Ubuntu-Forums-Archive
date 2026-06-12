---
title: "Dependency."
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-06
>  james@ubuntu:~/Desktop$ sudo dpkg -i skype_1.2.0.18-1_i386.deb
Selecting previously deselected package skype.
(Reading database ... 59197 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
skype
james@ubuntu:~/Desktop$


How'd I fix this?

---

### Post by tokyovigilante on 2006-01-06
sudo apt-get install libqt3-mt
sudo dpkg --force-depends -i skype_1.2.0.18-1_i386.deb

---

### Post by Jimmey on 2006-01-06
Still getting the same error message. :S

---

### Post by tokyovigilante on 2006-01-06
Did you use the --force-depends option?

---

### Post by Jimmey on 2006-01-06
Oh, sorry, yeah, I got it. Thanks.

---

### Post by tokyovigilante on 2006-01-06
The problem you're having is that Skype is looking for the package libqt3c102-mt, which are the QT libraries (part of KDE). Ubuntu has renamed this libqt3-mt, and since you're using the Debian Skype package, it's failing because of this name difference. The package is available, so using the --force-depends option when installing Skype will get it to ignore the issue. 

Once it installs it will find the libraries and should be happy. 
Just give this
```
sudo dpkg --force-depends -i skype_1.2.0.18-1_i386.deb

```a go

---

