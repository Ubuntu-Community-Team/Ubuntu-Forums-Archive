---
title: "GDebi Package Installer"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-08-02
I had GDebi Pakage Installer freeze up my computer. I had to shut the power off in order to fix it. Now when I try to install anything using it I get

Only one software managment tool is allowed to run at the same time.


And then it will not install. How do I fix this? Please keep in mind I am new. Thank you.


Malice

---

### Post by atomkarinca on 2007-08-02
are you sure synaptic package manager or add/remove or automatix isn't also running?

---

### Post by frodon on 2007-08-02
The problem should be that rebooting your system gdebi should not have had the time to release its root rights and now your system seems to believe that gdebi is still opened and using its root rights.
Or like said in the post above you may just have synaptic or a package manager opened.

Try to run this command in a terminal if you still have the problem :
```
sudo dpkg --configure -a
```

---

### Post by xxix on 2007-08-06
I just had the same issue. Thanks!

---

