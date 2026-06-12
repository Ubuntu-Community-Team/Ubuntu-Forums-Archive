---
title: "Downloading and Running Firefox"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-28
It's a stupid question, but it needs an answer.  I am not the biggest fan of Konqueror, and I would much rather have firefox running.  Because kubuntu only has Konqueror, I need to get Firefox.  Thanks.

---

### Post by cptjaben on 2006-10-28
I followed [this thread ]("http://ubuntuforums.org/showthread.php?t=151179&highlight=firefox+install+script") and found that it worked quite well, I believe edgy comes with the new firefox, maybe not if your using kde, i don't know.

---

### Post by firebirdworks on 2006-10-28
Sorry, I'm using dapper drake.  It didn't work for Kubuntu.

---

### Post by Peter41az on 2006-10-28
well my easy way was to load automatix ([www.getautomatix.com](www.getautomatix.com)) and among all the other goodies it provides, is firefox :)
actually im typing this on firefox now :)

---

### Post by NeoLithium on 2006-10-28
in a terminal window, you should be able to get it through the repositories with ```
 sudo apt-get install firefox 
```

Getting automatix also allows it to be quite easy as well; including java, and other plugins with minimum setup. You can check out the [automatix homepage]("http://www.getautomatix.com") for that type of installation for stuff.

---

### Post by esaym on 2006-10-28
hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

---

### Post by brn on 2006-10-29
This might do:  System > Administration  > Synaptic Package Manager... Give your password and when the screen appears choose "Status".  Click on "Not Installed".  You should find Firefox.  Mark for installation and proceed.

---

### Post by firebirdworks on 2006-10-29
> **NeoLithium said:**
> in a terminal window, you should be able to get it through the repositories with ```
 sudo apt-get install firefox 
```

Getting automatix also allows it to be quite easy as well; including java, and other plugins with minimum setup. You can check out the [automatix homepage]("http://www.getautomatix.com") for that type of installation for stuff.

ERRORS!!!
matt@Home:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnss3
E: Package firefox has no installation candidate
matt@Home:~$

---

