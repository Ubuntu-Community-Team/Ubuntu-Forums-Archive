---
title: "[SOLVED] I think I messed up the updates :("
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by RonB123123 on 2006-07-30
I didn't know how to uninstall WINE, WineTools, or Easy Ubuntu, so I just got rid of the 2 packages of wine in the synaptic packet manager and deleted the repositories for wine, and easy ubuntu i just deleted the folder and files.

Then I tried to check for updates, and ubuntu gave me these errors. And yes I could connect to the internet, and I also tried without a firewall. :(

[img]http://img155.imageshack.us/img155/4258/screenshothn2.png[/img]

Reply back soon, thank you.

---

### Post by PingunZ on 2006-07-30
Ok try edit your sources.list 
  ```
   sudo gedit /etc/apt/sources.list
     create a sources.list [here]("http://www.ubuntulinux.nl/source-o-matic") ( just copy paste )
     then save the file and do
     sudo apt-get update
```
if that doesnt work the problem is with your internet conection.

---

### Post by RonB123123 on 2006-07-30
The sources file is fine. I replaced it with the original, and here is my sources.list file. 

```

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
 
## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
# or updates from the Ubuntu security team. 
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
 
deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

I think it was wine because they said something about uninstalling libgtk1.2. When I uninstalled that, that is when things messed up. I can connect to the internet just fine, and visit web pages and all, I just can't do automatic updates or connect to the internet with bittorrent. 

I tried to install that lib file using the terminal and the synaptic packet manager, but I got deb errors, because the terminal can't access the internet. I tried to reinstall it by running this command.
```
 sudo apt-get install libgtk1.2
```

:(

---

### Post by RonB123123 on 2006-07-30
please help.

I was able to install that lib file, but it wasn't that that was causing the problems. I fear I will have to reinstall ubuntu no matter what, unless I get help. So please help me. [img]http://ubuntuforums.org/images/icons/icon8.gif[/img]

Is there anyway to restore Ubuntu? I just need to take it back a day or two.

---

