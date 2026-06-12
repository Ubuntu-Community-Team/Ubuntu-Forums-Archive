---
title: "Where do I go to make a feature request?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2007-11-30
Where do I go to make requests for pacakges that aren;t in the repos?  For example, I'd like to see e16 in the official Ubuntu  repositories.  e16 is stable: [http://www.enlightenment.org/p.php?p=download&l=en](http://www.enlightenment.org/p.php?p=download&l=en)

Also, Warsow is out of date.  I just installed 0.32, when the official webste says that the latest current release is 0.33.  I can't play my games because it is out dated D=

---

### Post by Tom Mann on 2007-11-30
I understand e16 is in the repository listed as enlightenment. You just need to select it under synaptic or from a terminal type

sudo apt-get install enlightenment

Then you can select Enlightenment from the session menu on the login screen.

---

### Post by Drone4four on 2007-11-30
> **Tom Mann said:**
> I understand e16 is in the repository listed as enlightenment. You just need to select it under synaptic or from a terminal type

sudo apt-get install enlightenment

Then you can select Enlightenment from the session menu on the login screen.

```
drone4four@ubuntu:~$ sudo apt-get install enlightenment
[sudo] password for drone4four:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
enlightenment is already the newest version.
enlightenment set to manual installed.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libevas1-loader-eet libecore1-x libevas1-loader-gif
  libecore1-file libecore1-bin libcairo-jni libecore1-con libecore1-evas
  libevas1-loader-png libecore1-ipc libecore1-job libecore1
  libevas1-loader-jpeg libevas1-loader-svg libecore1-config
  libevas1-loader-xpm libevas1-loaders-all libgtk-jni libecore1-txt
  libcairo-java libglib-jni libbcprov-java libevas1-saver-jpeg
  libevas1-engine-software-x11 libevas1-engine-software-generic libglib-java
  libevas1-engine-buffer libecore1-fb libevas1-saver-eet libevas1-loader-tiff
  libgtk-java libevas1-saver-png libevas1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
drone4four@ubuntu:~$ 

```

It says e17 is already installed. I don't want e17.  I want e16.

---

### Post by Drone4four on 2007-12-24
Hmm, on another ubuntu PC, e16 installs just fine with sudo apt-get install enlightenment because i haven't added e17 repos to my source list.

---

### Post by smartboyathome on 2007-12-26
> **Drone4four said:**
> ```
drone4four@ubuntu:~$ sudo apt-get install enlightenment
[sudo] password for drone4four:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
enlightenment is already the newest version.
enlightenment set to manual installed.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libevas1-loader-eet libecore1-x libevas1-loader-gif
  libecore1-file libecore1-bin libcairo-jni libecore1-con libecore1-evas
  libevas1-loader-png libecore1-ipc libecore1-job libecore1
  libevas1-loader-jpeg libevas1-loader-svg libecore1-config
  libevas1-loader-xpm libevas1-loaders-all libgtk-jni libecore1-txt
  libcairo-java libglib-jni libbcprov-java libevas1-saver-jpeg
  libevas1-engine-software-x11 libevas1-engine-software-generic libglib-java
  libevas1-engine-buffer libecore1-fb libevas1-saver-eet libevas1-loader-tiff
  libgtk-java libevas1-saver-png libevas1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
drone4four@ubuntu:~$ 

```

It says e17 is already installed. I don't want e17.  I want e16.

That is weird, as it is now called e17-cvs, not enlightenment. Could you uninstall what you have right now (completely remove it in synaptic or purge it in the command line) and then install it again and see if that works?

---

### Post by ramkumail on 2007-12-26
sorry to disturb.  where and how can we file a package request or feature request?

---

