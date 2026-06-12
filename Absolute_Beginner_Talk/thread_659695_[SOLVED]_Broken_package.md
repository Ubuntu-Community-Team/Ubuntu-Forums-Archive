---
title: "[SOLVED] Broken package"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by danbar on 2008-01-06
You have one package broken. Use the broken filter to locate it. How do I find the broken filter? thanks

---

### Post by empthollow on 2008-01-06
in synaptic go to Edit->Fix broken packages or in terminal type
```
sudo apt-get -f install
```

---

### Post by danbar on 2008-01-06
This is what I got......Thanks for your time!


~$ sudo apt-get -f install
[sudo] password for xxxxx:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  skype-common
The following NEW packages will be installed:
  skype-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2074kB of archives.
After unpacking 5059kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  skype-common
Install these packages without verification [y/N]? N
E: Some packages could not be authenticated

---

### Post by empthollow on 2008-01-06
if you want it to install you have to put "y" after install without verification.

---

### Post by danbar on 2008-01-06
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  skype-common
The following NEW packages will be installed:
  skype-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2074kB of archives.
After unpacking 5059kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  skype-common
Install these packages without verification [y/N]? y
(Reading database ... 151250 files and directories currently installed.)
Unpacking skype-common (from .../skype-common_2.0.0.27-0medibuntu1_all.deb) ...
Setting up skype-common (2.0.0.27-0medibuntu1) ...
Setting up skype (2.0.0.27-0medibuntu1) ...
xxxxx@xxxxx-desktop:~$ 

Is it ok now because there is no orange colour anymore telling me to upgrade the system.

---

### Post by danbar on 2008-01-06
Is it ok now because there is no orange colour any more telling me to upgrade the system?

---

### Post by empthollow on 2008-01-06
i would say the problem was corrected because of the line:
"Correcting dependencies... Done"
unverified packages are just packages that come from repositories that are not officially supported.  i have never had an issue with unverified packages.

---

### Post by danbar on 2008-01-06
In my case I see that I'm having some problems whenever  I need to upgrade from medibuntu.  In this case I needed to upgrade skype.  Now I'm satisfied.  Many many thanks.

---

