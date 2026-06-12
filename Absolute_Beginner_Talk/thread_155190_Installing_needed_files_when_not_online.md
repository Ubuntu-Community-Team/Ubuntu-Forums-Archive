---
title: "Installing needed files when not online"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2006-04-04
This may sound so very simple for the people that know, but.......I have tried for some time to find out how you are able to install different files on Ubuntu that are necessary for you to get online.  Modem is the prob.  It all seems to work IF you are online but not so when you are not.  Any simple solution for this.  Help.  Using dialup modem.  Can't for the life of me able to figure out how to take info from memory stick, CD, or other storage forms and put it into Ubuntu.

---

### Post by shyopstv on 2006-04-04
To get it from a CD, you burn it to a CD using the computeryou can get online with, download what you need, burn it to CD, put the CD into your Ubuntu machine, copy and paste the files over into the home/username directory, go into terminal and type:

sudo dpkg -i filename

Termianl will then ask for your password (because you used sudo) and will install your file

---

