---
title: "certain pages wont load."
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by warrior24 on 2008-03-21
I am have a trouble logging into  certain pages [www.desertschools.com](www.desertschools.com)   and  [http://redbox.com/](http://redbox.com/)  but everything else works so far. I set ipv6 to true in firefox. One thing I noticed is I am using eth19 but in other computers It uses eth0. So I am stuck :confused: Here is what the error page looks like.

---

### Post by hhhhhx on 2008-03-21
well both those pages are flash-tastic, so do you have flash?

---

### Post by warrior24 on 2008-03-21
Yes but dont know the command to tell your which version.

---

### Post by warrior24 on 2008-03-21
any one please help

---

### Post by zakirs on 2008-03-21
did you install flash

---

### Post by warrior24 on 2008-03-21
Yes straight from there web site.  When I access  [www.desertschools.com](www.desertschools.com) from another Ubuntu computer for a split second a bar pops up telling me I don't have flash installed but then it goes away and  finishes loading. But on the computer it does not work at all on it wont  have the bar pop up telling me about flash.

---

### Post by warrior24 on 2008-03-21
here is a screen shot from a computer that it works on but still tells me this.


I am off to bed for now

---

### Post by warrior24 on 2008-03-21
bump

---

### Post by warrior24 on 2008-03-22
anyone maybe you guys can help he completely uninstall flash, then reinstall it.

---

### Post by jan quark on 2008-03-22
remove flash and reinstall it again with this command
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by warrior24 on 2008-03-23
I get this error

fern@fern-desktop:~$ sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
[sudo] password for fern:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.2kB of archives.
After unpacking 160kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
E: There are problems and -y was used without --force-yes
fern@fern-desktop:~$

---

### Post by warrior24 on 2008-03-23
I removed it but I still says I have version "You have version 9,0,115,0 installed" when I do a flash test page

---

### Post by warrior24 on 2008-03-24
bump please help:(

---

### Post by warrior24 on 2008-03-25
:(:(

---

