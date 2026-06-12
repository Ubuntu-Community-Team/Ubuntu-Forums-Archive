---
title: "ubuntu-desktop installation without internet connection"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kaysersoze on 2007-02-27
Hi, I have recently decided to switch from Windows to Linux. I have already installed the Ubuntu Desktop on my laptop and it is now my primary OS of choice. Then I installed Ubuntu Server 6.10 on one of my old desktop PCs to act as a file server. Unlike other distros such as Fedora, I noticed though that it did not come with a Gnome interface for the server. I've search for appropriate install steps from this forum but the ones I found assumed that you have an internet connection (run apt-get update && apt-get install ubuntu-desktop)

My server however is not connected to the internet. Can anyone please advise how to install Gnome on a server without internet connection? I can download the required files from another PC. If you can put in simple "newbie" terms, it would be much appreciated. The version I have is ubuntu linux server 6.10, newly installed, default and no other configuration changes made yet.

thanks

---

### Post by taurus on 2007-02-27
Insert the desktop CD (LiveCD) into the drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by kaysersoze on 2007-03-05
Thanks...

after inserting the live cd, and running the above commands, I received an error saying it could not find the package "ubuntu-desktop"

btw, when do you use apt-get and when do you use aptitude to install apps? Is there any advantage over the other?

---

