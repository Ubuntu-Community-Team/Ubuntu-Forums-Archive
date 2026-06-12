---
title: "How to Add A Repository in sources.list.d"
date: 2011-07-23
forum: Any Other OS
---

### Post by Sef on 2011-07-23
I have installed Debian 6.02 and need want to add opennms. The directions say to add it to the /etc/apt/sources.list.d repository, which I can get to, but I cannot figure out how to write to it. So how can i write to it? Thank you in advance.

---

### Post by 23dornot23d on 2011-07-23
You would normally add it too the sources.list

**gksu gedit /etc/apt/sources.list**

the souces.list.d is usually a directory .....

Although [there is this thread on it ]("http://ubuntuforums.org/showthread.php?t=116400")and if the list goes in that directory it has to end in  .list

---

### Post by hhh on 2011-07-23
To add what 23d said, open you Run dialog (Alt+F2) and enter...
```
gksu nautilus
```... navigate to /etc/apt/sources.list.d, create a file named opennms.list, copy/paste the deb sources into it, save the file and close Nautilus and your text editor. Add the signing key by running in a terminal...```
wget -O - http://debian.opennms.org/OPENNMS-GPG-KEY | sudo apt-key add -
```... then update your sources and install opennms, again in a terminal...```
sudo apt-get update && sudo apt-get install opennms
```

---

### Post by Sef on 2011-07-25
Thank you both of you. I got it installed, although I have to run as root for it to run.

---

