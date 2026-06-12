---
title: "Installing Free Speech"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-05-28
Free Speech is an alternative to Festival the download page shows the two files:
FreeSpeech-0.1.2.tar.gz
FreeSpeech-0.1.2-linux_x86.tar.gz
Sound like this programme is now called Openmind  Speech.
Using sudo apt-get update and install did not get me a download so I tried Aptitude

clem@ubuntuhurricane:~$ sudo aptitude install openmind speech
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "openmind"
Couldn't find package "speech".  However, the following
packages contain "speech" in their name:
  libspeechd-dev speech-dispatcher-festival speech-tools
  speech-dispatcher-doc-cs libspeechd1 speech-tools-doc libgnome-speech3
  libgnome-speech3-dev speech-dispatcher speechd-el-doc-cs speechd-el
  cl-speech-dispatcher
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
clem@ubuntuhurricane:~$ sudo aptitude install freespeech
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "freespeech"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
clem@ubuntuhurricane:~$

As you can see no luck. Looking under repositories I have about 13 Ubantu 5.10 files either source files or updates. Not sure how to get access to other repositories or if I need to.

---

### Post by glotz on 2006-05-28
[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by Sef on 2006-05-28
> As you can see no luck. Looking under repositories I have about 13 Ubantu 5.10 files either source files or updates. Not sure how to get access to other repositories or if I need to.

Click on [Universe and Multiverse]("https://wiki.ubuntu.com/AddingRepositoriesHowto") to add them to your repositories.

---

