---
title: "Java"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2008-03-08
norgren@norgren-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 unixodbc
Suggested packages:
  equivs binfmt-support sun-java6-fonts libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 sun-java6-bin
  sun-java6-jre sun-java6-plugin unixodbc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.6MB of archives.
After unpacking, 96.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
norgren@norgren-laptop:~$ 

Does anyone know why I can't install Java?

---

### Post by taurus on 2008-03-08
What happens if you use capital Y instead of y for the answer?

---

### Post by gustasonfrever on 2008-03-08
Thats weird, this is all I get

norgren@norgren-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 unixodbc
Suggested packages:
  equivs binfmt-support sun-java6-fonts libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 sun-java6-bin
  sun-java6-jre sun-java6-plugin unixodbc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.6MB of archives.
After unpacking, 96.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
norgren@norgren-laptop:~$ norgren@norgren-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
bash: norgren@norgren-laptop:~$: command not found
norgren@norgren-laptop:~$ Reading package lists... Done
bash: Reading: command not found
norgren@norgren-laptop:~$ Building dependency tree       
bash: Building: command not found
norgren@norgren-laptop:~$ Reading state information... Done
bash: Reading: command not found
norgren@norgren-laptop:~$ The following extra packages will be installed:
bash: The: command not found
norgren@norgren-laptop:~$   gcc-3.3-base java-common libstdc++5 odbcinst1debian1 unixodbc
bash: gcc-3.3-base: command not found
norgren@norgren-laptop:~$ Suggested packages:
bash: Suggested: command not found
norgren@norgren-laptop:~$   equivs binfmt-support sun-java6-fonts libmyodbc odbc-postgresql libct1
bash: equivs: command not found
norgren@norgren-laptop:~$ Recommended packages:
bash: Recommended: command not found
norgren@norgren-laptop:~$   gsfonts-x11
bash: gsfonts-x11: command not found
norgren@norgren-laptop:~$ The following NEW packages will be installed:
bash: The: command not found
norgren@norgren-laptop:~$   gcc-3.3-base java-common libstdc++5 odbcinst1debian1 sun-java6-bin
bash: gcc-3.3-base: command not found
norgren@norgren-laptop:~$   sun-java6-jre sun-java6-plugin unixodbc
bash: sun-java6-jre: command not found
norgren@norgren-laptop:~$ 0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
bash: 0: command not found
norgren@norgren-laptop:~$ Need to get 33.6MB of archives.
bash: Need: command not found
norgren@norgren-laptop:~$ After unpacking, 96.2MB of additional disk space will be used.
bash: After: command not found
norgren@norgren-laptop:~$ Do you want to continue [Y/n]? Y
bash: Do: command not found
norgren@norgren-laptop:~$ Abort.
bash: Abort.: command not found
norgren@norgren-laptop:~$ norgren@norgren-laptop:~$ 
bash: norgren@norgren-laptop:~$: command not found

---

### Post by taurus on 2008-03-08
Reboot your machine.  Then, run these two commands.  Again, when it asks you if you want to install those packages, try using capital Y to see if it does it.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

