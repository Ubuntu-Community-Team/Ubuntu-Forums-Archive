---
title: "Problem Installing Beryl"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-07-04
When I try and Install Beryl, I get this problem:
```

ajeffreys@ajeffreys-laptop:~$ sudo apt-get install beryl beryl-manager emerald-themes 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
ajeffreys@ajeffreys-laptop:~$ 

```

Thanks for any help in advance :)
Ajeffreys

---

### Post by Analord on 2007-07-04
You might want to run &#8216;sudo apt-get -f install&#8217; to correct these...

---

### Post by ajeffreys on 2007-07-04
I tried that, but than i get this...

```
ajeffreys@ajeffreys-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
7 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 131533 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070703~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070703~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070703~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ajeffreys@ajeffreys-laptop:~$
```

---

### Post by Analord on 2007-07-05
You might wanna try running
sudo dpkg --configure -a
then sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

Also, i can see that you are using git version.. are those trevino repos ?
If so, u can try compiz-fusion by following this guide and everything in it (since beryl is discontinued and fusion offers almost everything from beryl)
[http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131)

But u shouldn't have any problems with beryl ... i recommend using beryl 0.2.1 form official ubuntu repos.

---

