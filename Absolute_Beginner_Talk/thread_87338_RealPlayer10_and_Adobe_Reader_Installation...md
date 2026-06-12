---
title: "RealPlayer10 and Adobe Reader Installation.."
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by sardopsycho on 2005-11-07
I am still a noob for Ubuntu, but I am getting the hang of it.  

However, I am having problems installing two applications.  

RealPlayer10GOLD.RPM
&
AdobeReader which is an RPM file.  

How do I go about installing these???

---

### Post by Xian on 2005-11-07
You need to read for topics in the [Ubuntu Wiki](http://www.ubuntulinux.org/wiki/) & [SEARCH](http://ubuntuforums.org/search.php) the forums. 
These topics have been covered often.

[How-To Install Realplayer10](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483) & [Adobe](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511063)
[How-To Install Adobe Reader](https://wiki.ubuntu.com/HowToGetAdobeAcrobatReaderWorking?highlight=%28adobe%29)

---

### Post by homerhomer on 2005-11-12
not supported but this seems to work for me

[http://ftp.debian-unofficial.org/debian/pool/non-free/r/realplayer10-binary-i386/realplayer10-binary_10.0.6+debian-1.unofficial.sarge.1_i386.deb](http://ftp.debian-unofficial.org/debian/pool/non-free/r/realplayer10-binary-i386/realplayer10-binary_10.0.6+debian-1.unofficial.sarge.1_i386.deb)

*note* I didn't have video until I turned of Acceleration *

---

### Post by seshomaru samma on 2005-11-13
[QUOTE=Xian]You need to read for topics in the [Ubuntu Wiki](http://www.ubuntulinux.org/wiki/) & [SEARCH](http://ubuntuforums.org/search.php) the forums. 
These topics have been covered often.

[How-To Install Realplayer10](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483) & [Adobe](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511063)
[How-To Install Adobe Reader](https://wiki.ubuntu.com/HowToGetAdobeAcrobatReaderWorking?highlight=%28adobe%29)[/QUOTE]


I followed the links and got this error message when trying to install acrobat :

```
kitty@zhou:~$ sudo apt-get install acroread acroread-debian-files
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Conflicts: acroread-debian-files (<= 0.0.8) but 0.0.8 is to be installed
E: Broken packages
```

any suggestions?

---

