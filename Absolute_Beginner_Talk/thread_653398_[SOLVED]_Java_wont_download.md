---
title: "[SOLVED] Java wont download"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Larsburham on 2007-12-29
Add and remove aplications says, 

"This application conflicts with other installed software. To install 'sun-java6-jdk' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

So I switch to Synaptic package manager to try and find out the problem, can't find what it is conflicting with so i try and download another version of Java. 

Try to install sun-java6-bin

Error message:
sun-java6-bin:
 Depends: sun-java6-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable
 Depends: libstdc++5  but it is not installable
 Depends: sun-java6-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable
 Depends: libstdc++5  but it is not installable

please help me!

---

### Post by blueridgedog on 2007-12-29
What do you get when you run the following command?

```
sudo update-alternatives --config java
```

After you run the command, just enter to keep the default, but post the output.

---

### Post by taurus on 2007-12-29
Check your repos to make sure you have all of them available.  In synaptic, go into Settings -> Repositories and mark on all except the last one, Sources code, and uncheck CDROM in the window.  Close that and then press Refresh.  Now, see if you can install java from synaptic again.

---

### Post by Larsburham on 2007-12-29
just changing those options in Synaptic package manager worked. 
Thank you very much!

---

