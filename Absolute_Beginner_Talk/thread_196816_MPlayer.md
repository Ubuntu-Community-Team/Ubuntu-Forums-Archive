---
title: "MPlayer"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-06-14
How do I install MPlayer to watch .wmv movies?

---

### Post by jasrog on 2006-06-14
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

---

### Post by Sutekh on 2006-06-14
Do install mplayer you need to enable the **multiverse** repository.   If you don't know how to add the multiverse repository, here's how.
  
  First you need to backup and edit the file that contains the repository sources.
  ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
sudo gedit /etc/apt/sources.list
``` When the text editor opens you need to uncomment (remove the # sign) these lines (if you are using Breezy you should have **breezy** in place of** dapper** in this file)
  ```
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe
  
  ...
  
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
``` and add **multiverse** to the end of them.
  
  They should look like this
  ```
deb http://archive.ubuntu.com/ubuntu dapper universe **multiverse**
deb-src http://archive.ubuntu.com/ubuntu dapper universe **multiverse**
   
  ...
  
deb http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
``` Save the file and then refresh the repositories list and then install mplayer using these commands
  ```
sudo apt-get update
sudo apt-get install mplayer
``` 
Or open Synaptic (System -> Administration) and click Reload, and then Search for mplayer, mark it for installation and click Apply.

You may (or may not) also need the w32codecs, which can be installed following the instructions from the [Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") page

---

### Post by harishg on 2006-06-14
Easiest way would be to install mplayer using synaptic and installing w32 codecs using easyubuntu.

---

### Post by Jagot on 2006-06-15
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

