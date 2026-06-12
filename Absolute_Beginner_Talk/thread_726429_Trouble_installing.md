---
title: "Trouble installing"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by BloodyFuel on 2008-03-16
I tried installing a few things in gutsy including the flash plugin for firefox
I tried doing it by using the firefox method (Using the "Install missing plugins feature)
I also tried using the terminal
Both times it said it couldn't find what I wanted
Please help me

Also if anyone has tutorials for absolute beginners to Ubuntu they would be much appreciated (:

EDIT: Tried installing Beryl using "wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -" and I got a 404 message

---

### Post by jan quark on 2008-03-16
for installing firefox use this command in terminal
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
for everything else look here
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by BloodyFuel on 2008-03-16
> **jan quark said:**
> for installing firefox use this command in terminal
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
for everything else look here
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

"Couldn't find package" ):

---

### Post by kellemes on 2008-03-16
[enable the multiverse repository.]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

Open a terminal window and start typing..
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kellemes on 2008-03-16
> **BloodyFuel said:**
> "Couldn't find package" ):

[enable the multiverse repository.]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

---

### Post by handydan918 on 2008-03-16
What exactly were you trying to install?

---

### Post by BloodyFuel on 2008-03-16
```
dan2@dan2-laptop:~$ dan2@dan2-laptop:~$ sudo apt-get install flashplugin-nonfree
 
bash: dan2@dan2-laptop:~$: command not found
dan2@dan2-laptop:~$ Reading package lists... Done
bash: Reading: command not found
dan2@dan2-laptop:~$ Building dependency tree       
bash: Building: command not found
dan2@dan2-laptop:~$ Reading state information... Done
bash: Reading: command not found
dan2@dan2-laptop:~$ Package flashplugin-nonfree is not available, but is referred to by another package.
bash: Package: command not found
dan2@dan2-laptop:~$ This may mean that the package is missing, has been obsoleted, or
bash: This: command not found
dan2@dan2-laptop:~$ is only available from another source
bash: is: command not found
dan2@dan2-laptop:~$ E: Package flashplugin-nonfree has no installation candidate
bash: E:: command not found
dan2@dan2-laptop:~$ dan2@dan2-laptop:~$ 
bash: dan2@dan2-laptop:~$: command not found
dan2@dan2-laptop:~$ 
dan2@dan2-laptop:~$ 
```

Just trying to install the flash plugin at the moment
But other things haven't been found either

---

