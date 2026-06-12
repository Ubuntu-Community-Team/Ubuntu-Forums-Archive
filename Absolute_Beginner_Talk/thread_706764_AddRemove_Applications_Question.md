---
title: "Add/Remove Applications Question"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by tufcamman on 2008-02-24
Hi, I recently installed 7.10 on my Thinkpad T30.  The installation went smooth and everything seems to be working well, even the wireless.  My only question is when I try to use the Add/Remove Applications tool it tells me that every single program is not supported by my computer type (i386).  I have version 6.x installed earlier and they all were happy with my computer then.  I have checked and update manager tells me everything is up to date.  Does anybody know why suddenly no software (not even Vim) is supported by my computer?  Any help would be great.  Thanks!

---

### Post by bobbybobington on 2008-02-24
Try clicking on the Preferences button in the Add/Remove window and make sure downloading from the internet is enabled.

If that doesn't work, try this workaround:
```
I got this error many times on 7.10 and this is what I did to resolve the issue.

Open a terminal and do the following, one line at a time.

sudo apt-get clean
sudo gedit /etc/apt/sources.list

Erase the content of sources.list and paste this in:

# Ubuntu supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

If you are not in the US and you want a local sources.list there is a generator here:
http://www.ubuntu-nl.org/source-o-matic/

Then simply do

sudo apt-get update
sudo apt-get upgrade -y

Reboot and try downloading the program again.
```

---

### Post by Joeb454 on 2008-02-24
Which version of Ubuntu did you install?

Was it amd64? or x86?

---

### Post by tufcamman on 2008-02-24
Thanks, I enabled online searching and everything works great now!

---

