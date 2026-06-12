---
title: "Sudo apt-get dist-upgrade question"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-08
Hi, the update manager of Dapper (not sure what the program command is) notified  me of updates.  One was a kernel update, and the rest seem to be related to my ATI Radeon Mobile.  However, the update manager says that it has "Held back" one update.  I did my update from the terminal to try to get this included, but it refuses to allow it.  Here is the output:
> 
user> sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Should I be concerned?  I have given up on 3d for my ATI RADEON mobility card, so I don't care about the package as long as my laptop display continues to work.

---

### Post by scrooge_74 on 2007-02-08
Are you planning to upgrade to Edgy?

If you are just updating the system then the correct command is 
sudo apt-get updated

follow by

sudo apt-get upgrade

Did you try the [this]("http://albertomilone.com/latestrepo.html") for your ATI card?

---

### Post by l951b951 on 2007-02-08
No, not planning on upgrading to edgy.  I used apt-get dist-upgrade because the update program told me to.  See the screenshot.

---

### Post by scrooge_74 on 2007-02-08
try sudo apt-get upgrade

Do you have the other repos available?

---

### Post by picpak on 2007-02-08
Try 

```
sudo apt-get install linux-restricted-modules-386
```

---

### Post by edu65 on 2007-02-08
There seems to be a problem with the latest kernel updates. Better to wait till it has been sorted out.

See

[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

> **picpak said:**
> Try 

```
sudo apt-get install linux-restricted-modules-386
```

---

