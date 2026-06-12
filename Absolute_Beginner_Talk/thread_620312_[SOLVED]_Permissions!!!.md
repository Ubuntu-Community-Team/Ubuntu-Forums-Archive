---
title: "[SOLVED] Permissions!!!"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by banda on 2007-11-22
there is a program i tried installing with its deb. the installation went fine
but now whenever i open synaptic i get the error message 
> 
E: The package awcommon needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

after this synaptic closes on it own

trying apt-get remove <package name> gives me :
> E: The package awcommon needs to be reinstalled, but I can't find an archive for it.

i have tried pasting the deb file from which i installed in /var/cache/apt/archives but i still get the same error

when i just double click the deb file i get 
> the package might be corrupted or you do not have the permission to open this file . check the permission on the file.

i do gksudo nautilus and try to change the permissions but it won't let me.....

what could be the reason for all this ... how can i fix it??...
this is a new installation of gutsy so there is not a big probability to have messed something up earlier

---

### Post by stanigator on 2007-11-22
Have you tried using the command sudo instead in terminal?

---

### Post by banda on 2007-11-22
to change the permissions?? 
i do not know the command for doing that :(

---

### Post by banda on 2007-11-22
<bump>

i really don't want to do a reinstall of ubuntu !!

---

### Post by banda on 2007-11-22
<bump> X2

---

### Post by philinux on 2007-11-22
sudo apt-get remove <package name>

---

### Post by spiderbatdad on 2007-11-22
```
sudo chmod 777 yourpathtofile
```

---

### Post by spiderbatdad on 2007-11-22
```
cd directoryoffile
ls -l 
```

this will show you current permissions. 
maybe check out this tutorial on permissions:[http://lowfatlinux.com/linux-chmod-chown.html](http://lowfatlinux.com/linux-chmod-chown.html)

---

### Post by banda on 2007-11-22
@philinux 
i already did that.. error in orignal post

@spiderbatdad
thanks for ur reply.. i tried chmod 777 for my file then did ls-l in the directory but it still displays "root" in front of the file!

---

### Post by banda on 2007-11-22
i have also tried the following command

> sudo dpkg --configure -a

which too does not solve the problem

---

### Post by bodhi.zazen on 2007-11-22
sudo dpkg -r awcommon

---

### Post by philinux on 2007-11-22
Search the forums is a good tool

[http://ubuntuforums.org/showthread.php?t=545055&highlight=awcommon+apt](http://ubuntuforums.org/showthread.php?t=545055&highlight=awcommon+apt)

[http://ubuntuforums.org/showthread.php?t=545055&highlight=awcommon+apt](http://ubuntuforums.org/showthread.php?t=545055&highlight=awcommon+apt)

---

### Post by banda on 2007-11-22
the problem i was facing with changing the permission was because the file was on ntfs partition s o that is SOLVED

but i can still not open synaptic.. it still displays the same error... updates are not working either

---

### Post by banda on 2007-11-22
...
> $ sudo dpkg  --force all -r awcommon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 127874 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon

---

### Post by banda on 2007-11-22
synaptic is working again after removing the entry for awcommon from /var/lib/dpkg/status

thanks for providing the link to the thread philinux and everyone else who helped!

mods please change the title to indicate SOLVED :)

---

### Post by philinux on 2007-11-22
Cheers - you mark it solved yourself by the way.

Thread tools drop down menu.

Seems that awcommon causes some headaches. I remembered I'd seen it before.

---

