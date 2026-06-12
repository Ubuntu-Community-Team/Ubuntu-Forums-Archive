---
title: "Install problems on flash player"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Rufi0h on 2007-06-16
So i am trying to install flash player to watch youtube and it keeps screweing up on me. it says

```
root@mark-desktop:/home/mark# rpm -Uvh <rpm_package_file>
-bash: syntax error near unexpected token `newline'
root@mark-desktop:/home/mark# # rpm -Uvh <rpm_package_file>
root@mark-desktop:/home/mark# yum install flash-plugin
Warning, could not load sqlite, falling back to pickle
Setting up Install Process
Setting up repositories
No Repositories Available to Set Up
Reading repository metadata in from local files
Parsing package install arguments
No Match for argument: flash-plugin
Nothing to do
root@mark-desktop:/home/mark# cd /home/mark/install_flash_player_9_linux
root@mark-desktop:/home/mark/install_flash_player_9_linux# pwd
/home/mark/install_flash_player_9_linux
root@mark-desktop:/home/mark/install_flash_player_9_linux# ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

root@mark-desktop:/home/mark/install_flash_player_9_linux# 

```

This is what i get when i try to do it

i think the first way was me trying to install it with yum, please help me.

---

### Post by finer recliner on 2007-06-16
assuming your using *buntu and not a red hat based distro, you cannot use yum or rpm options. you should use the .tar.gz option

yum is the package manager for red hat (aptitude is the package manager for ubuntu)

.rpm are autoinstallers for red hat distros. .deb is the auto installer for debian based distros (ubuntu is debian based)

---

### Post by Rufi0h on 2007-06-16
i am using Ubuntu and i also tried to do the tar.gz. install and it didn't work

when i try it says

[B]ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.[/B]

any suggestions

---

### Post by Vague on 2007-06-16
Well, I haven't had to do it myself, but there's a tutorial on how to install the Flash Player in 64-bit Ubuntu in this thread: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

---

### Post by Rufi0h on 2007-06-21
thanks a ton, it worked.

---

