---
title: "can't install programs"
date: 2011-11-26
forum: Any Other OS
---

### Post by 4x40ranger on 2011-11-26
Hello I am running zorin-os5 witch is based off of ubuntu 11.04 when I try to install a program i get the error 
W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I am a beginner to linux any help is appreciated

---

### Post by ajgreeny on 2011-11-26
If you remove any files in **/var/lib/apt/lists/partial/** and then run ```
sudo apt-get update
```  you may solve the problem.

---

### Post by oldos2er on 2011-11-26
Moved to Other OS/Distro Talk.

---

### Post by sophia911 on 2011-11-27
#2 is good answer . 
Try it .

---

### Post by 4x40ranger on 2011-11-28
that was it thank you it took me a few tries to delete that directory but it is working now.

I had to use
[B]sudo rm -r /var/lib/apt/lists/partial/
sudo rmdir [/B][B]/var/lib/apt/lists/partial/
sudo apt-get update

[/B]

---

