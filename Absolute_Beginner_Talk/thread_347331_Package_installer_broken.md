---
title: "Package installer broken"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by quercusrobur2002 on 2007-01-27
Hope somebody can help, my package installer seems to be broken. After trying to perform an update of available packages I recieved the following error message;

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

When I typed in the suggested command in the terminal I got this message;

"graham@graham-laptop:~$ sudo apt-get install -f
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
graham@graham-laptop:~$"

I then closed down the PC and rebooted, but the same problems and messages persist. Furthermore, on booting up I got an error message "The panel encountered a problem while loading "OAFIID:TomboyApplet".",  and Tomboy notes (where i keep all my log in passwords, etc) will no longer start up and it's shortcut is no longer on my top panel.

any suggestions for fixing these problems?? I'm using Dapper Drake

---

### Post by jvc26 on 2007-01-27
> 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This error is usually caused when you have synaptic package manager/update manager/terminal doing sudo apt-get commands open at the same time, as they are all trying to access the same stuff, and so one locks the others out. The answer to that is, try again, close all windows bar the terminal, and then type:
```

sudo apt-get install -f

```
And see if that works?
Il

---

### Post by quercusrobur2002 on 2007-01-27
OK, I typed in that command "sudo apt-get install -f", this time I got the message below, which isn't actually very helpful to me as the Package manager still seeems to be broken. Hovering the mouse over the Package Manager icon in my top panel  gives me a suggestion to run Package Manager from a right click, with the error message.  'Error:BrokenCount > 0'

Still baffled!

graham@graham-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libc6-i686
The following packages will be upgraded:
  libc6-i686
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
2 not fully installed or removed.
Need to get 0B/1078kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up locales (2.3.18.1) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on locales (>= 2.3.11); however:
  Package locales is not configured yet.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 libc6
E: Sub-process /usr/bin/dpkg returned an error code (1)
graham@graham-laptop:~$

---

### Post by bigken on 2007-01-27
in synaptic look for broken packages and remove them 

system/administration/synaptic/custom filters/broken

---

### Post by quercusrobur2002 on 2007-01-27
Hi BigKen, tried that, the flter returns no matches. I also tried the 'fix broken packages' command from the 'edit' menu, whcih tells me that it has "Successfully fixed dependency problems", and that there are "0 broken packages", but still the problem persists...

---

### Post by quercusrobur2002 on 2007-01-27
Tried again, this time was able to remove the broken package, however when i then tried to install a program using Package Manager this time I got this error message;

E: locales: subprocess post-installation script returned error exit status 139
E: libc6: dependency problems - leaving unconfigured

Also got the same message complaining about libc6 when I tried to use the update manager from the top panel...

Any other suggestions??? What is libc6 and how do I fix it???

---

