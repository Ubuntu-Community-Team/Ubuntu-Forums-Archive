---
title: "apt-get update hangs at 66%"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by gurustered on 2007-09-26
Hi all, I am new to Ubuntu (and Linux for that matter). I am running to in problems while trying update (apt-get update).

I am running Ubuntu Server (6.06) in VMWare Server - bridged mode.

Can I manually download the updates, burn them to CD and update that way? 

Thanks,

---

### Post by KIAaze on 2007-09-26
> Can I manually download the updates, burn them to CD and update that way? 
Yes you can.

See here: [http://ubuntuforums.org/showpost.php?p=2825763&postcount=9]("http://ubuntuforums.org/showpost.php?p=2825763&postcount=9")
(I don't know how to do that on a server without GUI however...)

Otherwise, you can also download packages manually from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/").#

To install them, simply double-click on them.
Or by command-line:
```
sudo dpkg -i package.deb
```

Also make sure to update the package list in synaptic and check the /etc/apt/sources.lst file. Maybe it will help you solve the hanging problem.

---

### Post by gurustered on 2007-09-26
Thanks, I am usine CLI only. Probably not a good idea since I'm trying to learn this.:)

---

### Post by KIAaze on 2007-09-26
Well, you can always use "lynx" to find and download the .deb files. ^^
Or use "wget" to download them if you have the full URL. ;)

---

