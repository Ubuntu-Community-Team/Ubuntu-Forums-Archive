---
title: "E: dpkg was interrupted (Second-Life)"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by banished_one on 2008-02-11
I was trying to intall secondlife then my connection died, then the package installer froze so i restarted the ubuntu. Now when i try to install something via package installer i get an

The package might be corruptted or you are not allowed to open the file. Check the permissions of the file.

When i try to run Synaptic Package manager i get an 

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried this but didnt help

sudo dpkg --configure -a 
sudo apt-get clean all
sudo apt-get update

Also this

aras@aras-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

What can i do to fix this

---

### Post by hyper_ch on 2008-02-11
download the secondlife-install (.deb) file and put it where all the other .debs are downloaded to.

---

### Post by spiderbatdad on 2008-02-11
```
sudo apt-get install -f
```

---

### Post by banished_one on 2008-02-11
> **hyper_ch said:**
> download the secondlife-install (.deb) file and put it where all the other .debs are downloaded to.

im downloading all the debs to desktop and second-life deb is there right now too

and i tried 

aras@aras-desktop:~$ sudo apt-get install -f
[sudo] password for aras:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

---

### Post by hyper_ch on 2008-02-11
you need to put it into the archive folder where all other downloaded .debs are...

---

### Post by banished_one on 2008-02-11
hmm where is that :(

---

### Post by Majorix on 2008-02-11
/var/cache/apt/archives

---

### Post by FuturePilot on 2008-02-11
Try this
```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```
This will basically force remove it. Then you can try to reinstall it if you want.

---

### Post by banished_one on 2008-02-11
> **FuturePilot said:**
> Try this
```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```
This will basically force remove it. Then you can try to reinstall it if you want.

this solved it many thanks

---

