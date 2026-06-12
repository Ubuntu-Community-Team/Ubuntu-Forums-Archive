---
title: "finger error"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by rocket76 on 2007-12-24
I am unable to install anything in Gutsy. This is a fresh install. Whenever I try to install anything like vlc or startupmanager from the Synaptic Package Manager, the files get downloaded. however, the installation fails with errors related to finger package. I get something like this:

"E: /var/cache/apt/archives/imagemagick_7%3a6.2.4.5.dfsg1-2ubuntu1_i386.deb: unable to open files list file for package `finger'"

---

### Post by Maxtorm on 2007-12-24
It could be that your apt cache is corrupt. Try the following: ```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```
Then attempt to install one of the packages that failed.

---

