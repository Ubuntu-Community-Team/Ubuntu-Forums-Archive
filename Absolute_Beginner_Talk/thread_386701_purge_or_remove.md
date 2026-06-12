---
title: "purge or remove?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mills on 2007-03-17
hi all,

got vmware installed but messed it up so i need to get rid of it and start from scratch, but iam not sure how exactly seeing as its spread over so many dirctories,

should i remove or purge and what exactly is the difference and also what is the code for for purge if i should use that? (and remove for that matter)

---

### Post by TheRingmaster on 2007-03-17
how did you install vmware? and what exactly is your problem with it?

---

### Post by AtrejuT on 2007-03-17
purge also removes any configuration files, while remove removes the software but no configuration files (AFAIK). So if you want to start out fresh, you probably want to purge things.

atreju

---

### Post by mills on 2007-03-17
installed it via this guide

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=install+vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=install+vmware)

and i messed it up when trying to sort a sound problem , havent got a clue what i changed but the error i get with it now is

Unable to change virtual machine power state: Could not execute /usr/lib/vmware/bin/vmware-vmx.

and after googling and searching i couldnt find an answer so i figure its best to just reinstall it

---

### Post by mills on 2007-03-17
so would the code to purge be

sudo apt-get purge vmware?

or

sudo aptitude purge vmware?

---

### Post by v8YKxgHe on 2007-03-17
```

sudo apt-get remove --purge vmware
```

Regards,

---

### Post by Kateikyoushi on 2007-03-17
Both would do the trick, to learn the difference I would recommend to read this. [LINK]("http://www.psychocats.net/ubuntu/aptitude")
In  a nut shell aptitude knows more.

---

### Post by mills on 2007-03-17
i tried your code Alexc but i got this

alex@alex-desktop:~$ sudo apt-get remove --purge vmware
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware

so i tried aptitude and got this

alex@alex-desktop:~$ sudo aptitude --purge remove vmware
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find package "vmware".  However, the following
packages contain "vmware" in their name:
  vmware-player vmware-player-kernel-modules-2.6.15-23 
  vmware-player-kernel-modules-2.6.17-10 
  vmware-player-kernel-modules-2.6.17-11 vmware-player-kernel-source 
  vmware-player-kernel-modules xserver-xorg-video-vmware 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

should i purge the 4 vmware parts seperately?
if so in any particular order?

---

### Post by mills on 2007-03-17
ok i tried purging the top one

```
sudo aptitude --purge remove vmware-player vmware-player-kernel-modules-2.6.15-23
```

but got this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

what should i try now?

---

### Post by mills on 2007-03-17
sorry but really need to bump this :(

---

### Post by mills on 2007-03-17
seriously confused now... i just went throught the 4 vmware parts mentioned above trying to purge them one by one  the only one i could purge was 

vmware-player-kernel-modules xserver-xorg-video-vmware

but vmware is still there, am i going to have to completely reinstall ubuntu just to reinstall vmware?

---

### Post by mills on 2007-03-17
ok iam getting seriously confused frustrated and stressed

i tried 
```
$ sudo -i
# vmware-uninstall-mui.pl
# vmware-uninstall.pl
```

and 
```
sudo vmware_uninstall.pl
```

now when i go to luanch vmware i get

```
Failed to execute child process "vmware" (No such file or directory)
```

 i still have thousands of vmware files... am i missing something really simple or is it impossible to uninstall vmware.. should i just try reinstalling it without uninstalling it 

any hints tips and scraps are much appreciated

---

