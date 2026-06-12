---
title: "How to Install Programs"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by cornellpd on 2008-01-26
Hi-thanks for reading-I'm trying to install Limewire, or Frostwire-or for that matter anything.  New to linux, and not sure how to do this-I can download the programs, but can't install them, or doubleclick and they come up-can't even log in as su-do I need to run something to erase oem config, and make me the administrator of the computer?Thanks for the help

---

### Post by hyper_ch on 2008-01-26
Use "Add/Remove" or "Synaptic" from your program's list.

And if you are the first user that was setup (during installation) the admin password is the same as your password. So when prompted to give admin password use yours.

---

### Post by reeseslover531 on 2008-01-26
not sure what the problem is, but there is a howto located here [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire) that you might find useful.  It seems to cover pretty much everything.

---

### Post by Kilz on 2008-01-26
[This page may be of help.]("http://www.monkeyblog.org/ubuntu/installing/") It has a great section on Synaptic.

---

### Post by Crumpets and Jam on 2008-01-26
[This .deb file]("http://www.limewire.com/LimeWireSoftLinuxDeb") is the official LimeWire installer for Ubuntu and Debian. It is from there site.

Download it to the desktop or where you like, after it has saved, simply 'double-click' it like you would in Windows. It will then install LimeWire for you.

---

### Post by cornellpd on 2008-01-26
Thanks for all of the replies, I think the majority of the problem is the fact that I have the wrong version of Java installed.  After I doubleclick on the icon on the desktop (file), I get an error in the install package tool that say something like "dependence not satisfied...java this and that...."  So I guess I need to download the latest version of the runtime environment-this is something I tried to do before without success.  One time I tried it and it said the file was corrupt.  Any tips on getting the jre file that is good?  Thanks again.

---

### Post by Crumpets and Jam on 2008-01-27
I think installing the Restricted Formats package will solve this problem. This package contains all the required things to play and use non - opensource formats like WMV, DVDs and things like that. I think Java is in there to.

In Ubuntu 7.10

Go to **Applications --> Add/Remove**
Set Show: to **All available applications**
Search for **ubuntu-restricted-extras** and install it. Note that there is also **xubuntu-restricted-extras** and **kubuntu-restricted-extras**

**OR** open up the terminal and execute the following command:

**sudo apt-get install ubuntu-restricted-extras**

---

