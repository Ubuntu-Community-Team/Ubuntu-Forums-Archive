---
title: "Where are the packages downloaded  ?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-23
There is no problem here i just would like to know when i goto synaptic and choose a package to install 
1- Where is it downloaded (the package files themselves)?
2- After installation are the installation  files removed?
3- Where are the packages installed on what directory ?
i tried looking under /usr but found many folders which ones ?

---

### Post by JNowka on 2006-09-23
The packages are downloaded to the /var/cache/apt/archives folder.  if you don't look forward to installing them over again if you have to install Ubuntu, then it is a good idea to burn these to a cd.

---

### Post by D_frag on 2006-09-23
Thanks JNowka 
i still need to know where the packages are installed  
and i just have one more question ..i know the swap partition holds virtual memory ..but can anyone give examples ??? In addition whats the purpose of the ext3 partition  what doe sit hold ?

---

### Post by lamego on 2006-09-23
D_frag,
files are installed over several differente dirs according to their type, read more about the linux tree here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

Uh, examples of what ? Swap is used for when there is not enough physical memory available, running programs which are not active will be moved to the swap memory (disk).


Ext3 is a partition type, if you are refering to the / partition it holds your entire system and your users data, unless you have created a split ext3 partition for it.

---

### Post by harlan on 2006-09-23
D_frag:
To find out where a package is installed you can open synaptic (system/administration/synaptic) and search the package. Right click on it and select "properties". Then select the tab "installed files". There you will see the path to all the files of that package. Usually the executable file is in /usr/share.

---

