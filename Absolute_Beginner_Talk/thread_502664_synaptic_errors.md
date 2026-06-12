---
title: "synaptic errors"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by jakelaptop on 2007-07-16
I'm on my 3rd day of linux here, and I seeem to have already managed to bring everything to a screeching halt.
When trying to add or remove a package in synaptic, after clicking "apply" the application add or removal progress bar window flashes quickly on the screen, then dissappears, and the bottom bar of synaptic says that whatever tasks I had checked are still waiting to be applied(i.e. "6 files to remove")
What am I doing wrong here? Or let me know if there is any more information you need to diagnose this problem.

---

### Post by randytuggle on 2007-07-16
Without being a total pro, I would suggest doing two things: 
1. Hit the reload button on the synaptic program window before choosing what to install AND
2. open terminal, (Applications>Terminal) type in
sudo apt-get update

and let the system update program packages it needs to get the job done.

Hope that helps you!

---

### Post by Nythain on 2007-07-16
what does it say if you open a terminal and type:
```

sudo apt-get update
sudo apt-get install <whatever package>

```

---

### Post by jakelaptop on 2007-07-16
this is what i get after doing the update:

jwertz@jwertz-laptop:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libbcprov-java libcairo-java libcommons-cli-java libglib-java
  libgnucrypto-java libgtk-java libgtk-jni liblog4j1.2-java libseda-java
  libswt3.2-gtk-java libswt3.2-gtk-jni
Suggested packages:
  libbcprov-java-doc libgnumail-java
Recommended packages:
  azureus-gcj libbcprov-java-gcj libcairo-java-gcj libglib-java-gcj
  libswt3.2-gtk-gcj
The following NEW packages will be installed:
  azureus libbcprov-java libcairo-java libcommons-cli-java libglib-java
  libgnucrypto-java libgtk-java libgtk-jni liblog4j1.2-java libseda-java
  libswt3.2-gtk-java libswt3.2-gtk-jni
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.1MB of archives.
After unpacking 15.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by jakelaptop on 2007-07-16
sorry, forgot to mention, if you;re wondering why it says "had to get 0/12.1mbs" ... I believe its becasue I already downloaded the files in synaptic. 
I'm not having any trouble downloading files, it's just the unpacking or installing or whatever its called.

---

