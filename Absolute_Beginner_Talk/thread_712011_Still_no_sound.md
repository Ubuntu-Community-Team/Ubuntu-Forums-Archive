---
title: "Still no sound"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-03-01
I`m still trying to get sound working on a Toshiba laptop. I am trying to install the latest alsa drivers using these instructions.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
I`m getting stuck at this bit



Download the latest version of alsa from [WWW] Alsa project (driver, lib, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14. Please change this in accordance with the one you downloaded from the Alsa project site.

    *

      [WWW] alsa-driver
    *

      [WWW] alsa-lib
    *

      [WWW] alsa-utils

#

Setup installation directories


sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

I thought I was downloading the files to /downloads but I`m obviously not because I get this error.
cp: cannot stat `/home/rob/downloads/alsa*': No such file or directory

How do I download the files to the correct place so that 6 lines of code, used to set up installation directories above, work when I copy and paste.

Toshiba doesn`t like Ubuntu.
Oh well, at least I`m learning stuff:)

---

### Post by timbounceback on 2008-03-01
It probably downloaded to the desktop; you can either modify the commands to look for the file on the desktop, or copy the files into the downloads directory. Rememeber that Linux is case-sensitive!

---

### Post by nothingspecial on 2008-03-01
Thanks for the reply but I don`t think I understand how tho browse the file system in the terminal. The files are in "downloads" which is in "rob" which is in "home". The files are called
alsa-driver-1.0.16.tar.bz2
alsa-lib-1.0.16.tar.bz2
alsa-utils-1.0.16.tar.bz2

How do I modify the 6 lines of code in my original post so that they do what they are supposed to.

---

### Post by nothingspecial on 2008-03-01
I appologise. Your post answered everything> Very handy links at the bottom.
Also you were right, I`d called the file Downloads not downloads. Thankyou.

---

### Post by nothingspecial on 2008-03-01
Completed the instructions - still no sound. Oh well back to google/forums.

---

### Post by trdcelica on 2008-03-01
join the club

---

