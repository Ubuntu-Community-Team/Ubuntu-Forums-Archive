---
title: "error with a package install"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-12-01
the flashpluggin-nonfree didn't install correctly how do i fix this??
i've noticed when installing it it sat there for a long time i think it was waiting for a prompt from me but another screen never came up

E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by LLRNR on 2006-12-01
```
sudo aptitude remove flashplugin-nonfree
```or, if that doesn't work,```
sudo aptitude purge flashplugin-nonfree
```and then do```
sudo aptitude install flashplugin-nonfree
```HTH,

LLRNR

---

### Post by lime4x4 on 2006-12-01
john@john-edgy:~$ sudo aptitude remove flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  evince initramfs-tools 
The following packages will be REMOVED:
  flashplugin-nonfree 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 6808kB will be freed.
Writing extended state information... Done
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 flashplugin-nonfree
Aborted (core dumped)
john@john-edgy:~$ sudo aptitude purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  evince initramfs-tools 
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 6808kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
john@john-edgy:~$ Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by LLRNR on 2006-12-01
```
sudo aptitude remove -f flashplugin-nonfree
```or```
sudo aptitude purge -f flashplugin-nonfree
```The **-f** switch should force fixing broken packages...

LLRNR

---

### Post by lime4x4 on 2006-12-01
nope same errors

---

### Post by LLRNR on 2006-12-01
I assume you're using Gnome (i.e. Synaptic Package Manager). If this is the case, go to Synaptic and --- I don't remember quite well, since I run KDE --- you should look down in the "status bar", where you get the number of currently installed packages, the number of packages to be upgraded, removed etc. You should check if you have a broken package listed around and, if so, in the menus (I don't remember which one, though) you should see an option "Fix Broken Packages".

HTH,

LLRNR

---

### Post by lime4x4 on 2006-12-01
yes i i'm when i try to get synaptic to repair the broken package i get this


E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
\
And that's it.Doesn't even attempt to fix it

---

### Post by LLRNR on 2006-12-01
They say something [here](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3) about the flashplugin-nonfree... Not sure if it's gonna help though.

LLRNR

---

### Post by lime4x4 on 2006-12-01
well i fixed it and it may have not been the correct way but it worked

i edited the file /var/lib/dpkg/status 

and removed all refrence to the flashpluggin-nonfree

and that worked

---

### Post by theunseenpen on 2008-01-27
I've a fellow noob at Ubuntu/LInux, and I've been struggling through this Flash Player issue for at least two days, but alas...I've found a fix from [this]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890") website...though I dunno the exact process I used. [shrugs] I'll be more attentive next time hopefully, apologies for my lack of help, I'm just so overly excited to be able to use youtube once again...that's the only thing that spoiled me on XP :P

---

