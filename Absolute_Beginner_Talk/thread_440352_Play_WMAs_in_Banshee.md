---
title: "Play WMAs in Banshee"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-05-11
This is for any banshee users out there, how do I get WMA files to work in Banshee? Any help will be greatly appreciated because I have a lot of files in WMA and I like using Banshee

Thanks in advance

Simon North

---

### Post by Rescue9 on 2007-05-11
Try looking here. I'm not sure if you'll have to compile it yourself. but it may work

[http://banshee-project.org/forums/viewtopic.php?=&p=128](http://banshee-project.org/forums/viewtopic.php?=&p=128)

---

### Post by Seisen on 2007-05-11
You need to install the codecs, W32codecs are illegal so use at your own risk.

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

``` those are the repo's where the codecs are.

 Download needed gpg keys; e.g., use the following command for the PLF repository's gpg key: 

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Then ```
sudo apt-get update
sudo apt-get install  w32codecs
```

Let me know if that works

---

