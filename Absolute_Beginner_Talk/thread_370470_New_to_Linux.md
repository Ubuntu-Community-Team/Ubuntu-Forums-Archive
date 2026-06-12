---
title: "New to Linux"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Sovereign Entity on 2007-02-25
I have a dual boot system XP on the front end with a partition created by Ubuntu 6.6. My question is if I install 6.10 will it install over the previous version. Or do I have to uninstall or something.

---

### Post by aysiu on 2007-02-25
Do you want to install 6.10 over 6.06? If so, yes, that's possible. You can also upgrade to 6.10 if you have a fast internet connection or an Alternate CD for 6.10.

---

### Post by steve.horsley on 2007-02-25
You will need to use custom partitioning and tell it which partition to overwrite. I really can't remember if the GUI installer on the "desktop" CD can do this - you might need the "alternate" installer CD.

---

### Post by solar george on 2007-02-25
Ubuntu and most (if not all) linuxes can upgrade seamlessly with out wiping your previous config.

[http://ubuntuforums.org/showthread.php?t=284831]("http://ubuntuforums.org/showthread.php?t=284831")

---

### Post by aysiu on 2007-02-25
> **steve.horsley said:**
> You will need to use custom partitioning and tell it which partition to overwrite. I really can't remember if the GUI installer on the "desktop" CD can do this - you might need the "alternate" installer CD.
Both the Desktop and Alternate CDs allow custom use of partitions.

---

### Post by Sovereign Entity on 2007-02-25
I do have a fast internet connection and the upgrade is what i would like to do. I will take a look at the site

---

### Post by Sovereign Entity on 2007-02-26
Ok i tried the upgrade option  (gksu "update-manager -c")  a number of times but it didnt work. Now I have the alternate cd and hopefully i can boot from cd and have it installed in the correct place. I also notice that this cd dosent boot from windows.

---

### Post by aysiu on 2007-02-26
This is how you upgrade using the Alternate CD: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.dapper.list
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

---

