---
title: "Update Problems"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2008-02-04
System says it has updates available, but that there is an error:
> the error message was: 'error: brokencount > 0'

I run Synaptic and get this error:

> E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.6_i386.deb: subprocess new pre-removal script returned error exit status 102

Here is my output for 'Sudo apt-get install -f'

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
Need to get 0B/2850kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 97840 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.6_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas?

---

### Post by spiderbatdad on 2008-02-04
```
aptitude
```

This should allow you to locate and fix broken packages as  if synaptic were open, and you could select fix broken packages.

---

### Post by bladefallcon on 2008-02-05
> **spiderbatdad said:**
> ```
aptitude
```

This should allow you to locate and fix broken packages as  if synaptic were open, and you could select fix broken packages.

ok.....ummm...care to explain what im supposed to do with that?

---

### Post by oedha on 2008-02-05
just type it on terminal.......maybe you can fix it there

---

### Post by bladefallcon on 2008-02-05
> **oedha said:**
> just type it on terminal.......maybe you can fix it there

ok...let me rephrase...i am aware i need to type that into the terminal...i just have no idea what it is im looking at when i do, or what to do with it...

---

### Post by spiderbatdad on 2008-02-05
with your cursor, click on the word "search" the select "find broken"

---

### Post by bladefallcon on 2008-02-05
> **spiderbatdad said:**
> with your cursor, click on the word "search" the select "find broken"

ok....did that...still dont know what im looking at...

---

### Post by jan quark on 2008-02-05
what happens when you run this terminal command

```
sudo apt-get -f install
```

---

### Post by bladefallcon on 2008-02-05
> **jan quark said:**
> what happens when you run this terminal command

```
sudo apt-get -f install
```

try reading my post...the output of that command is there.

---

### Post by jan quark on 2008-02-05
run 

```
sudo dpkg --configure -a
```

---

### Post by bladefallcon on 2008-02-05
> **jan quark said:**
> run 

```
sudo dpkg --configure -a
```

i ran that....doesnt seem to have done anything...

---

### Post by Anicka on 2008-02-05
Try to uninstall samba```
sudo apt-get remove --purge samba
```If it doesn't work do```
sudo dpkg -P samba
```or it that doesn't work```
sudo dpkg -P --force-all samba
```. When you have uninstalled it, redownload the package. I don't know how to do it in apt-get, but this is how to do it in aptitude:```
sudo aptitude -d install samba
``` Thereafter try to install it with your favorite installer apt/aptitude/synaptic.

---

### Post by bladefallcon on 2008-02-05
> **Anicka said:**
> Try to uninstall samba```
sudo apt-get remove --purge samba
```If it doesn't work do```
sudo dpkg -P samba
```or it that doesn't work```
sudo dpkg -P --force-all samba
```. When you have uninstalled it, redownload the package. I don't know how to do it in apt-get, but this is how to do it in aptitude:```
sudo aptitude -d install samba
``` Thereafter try to install it with your favorite installer apt/aptitude/synaptic.

no such luck...here are my results:

```
blade@blade:~$ sudo apt-get remove --purge samba
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 53 not upgraded.
Need to get 0B of archives.
After unpacking 7258kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97839 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
blade@blade:~$ sudo dpkg -P samba
(Reading database ... 97839 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba

```

```
blade@blade:~$ sudo dpkg -P --force-all samba
(Reading database ... 97839 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba

```

---

### Post by Anicka on 2008-02-05
Found this [http://ubuntuforums.org/archive/index.php/t-179320.html](http://ubuntuforums.org/archive/index.php/t-179320.html) It is old, but the problem simular. The solution is to remove the "dangling symlink"```
cd /etc/rc2.d/
sudo rm K09samba
```After that```
sudo apt-get install --reinstall samba samba-common
```Good luck!

---

