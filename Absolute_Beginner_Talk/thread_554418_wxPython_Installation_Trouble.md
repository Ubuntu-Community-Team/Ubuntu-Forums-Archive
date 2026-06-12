---
title: "wxPython Installation Trouble"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-09-19
When I use this command in terminal:
sudo apt-get install python-wxgtk2.8 python-wxtools python-wxversion

It runs through the commands to start installing and then ends with this error message with out finishing the installation:

Setting up bcm43xx-fwcutter (006-1) ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   723  100   723    0     0   2264      0 --:--:-- --:--:-- --:--:--  117k
Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum f75a060f25225d1c920f85a946818301.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help anyone?
~J3ff

---

### Post by AlexKeaton on 2007-09-19
It seems as if the MD5sum dosn't match. You'll need to make it match for it to work.

---

### Post by beastrace91 on 2007-09-20
> **AlexKeaton said:**
> It seems as if the MD5sum dosn't match. You'll need to make it match for it to work.

What is the MD5 and how do I make it match so this will work?

~J3ff

---

