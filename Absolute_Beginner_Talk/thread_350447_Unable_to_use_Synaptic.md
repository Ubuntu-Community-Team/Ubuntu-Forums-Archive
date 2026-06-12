---
title: "Unable to use Synaptic"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by molex on 2007-01-31
molex@BlackMonster:~$ sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

Then when I try and open the .deb to reinstall, I am unable to. Suggestions?

---

### Post by Brunellus on 2007-01-31
sudo apt-get -f install

will atempt to fix any broken packages.

---

### Post by molex on 2007-01-31
molex@BlackMonster:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by molex on 2007-01-31
Is there a way a can remove this package from Synaptics local list of installed packages?

---

### Post by Brunellus on 2007-01-31
> **molex said:**
> Is there a way a can remove this package from Synaptics local list of installed packages?
the package manager is SYNAPTIC.  SynapticS is a type of touchpad and touchpad driver.  Thread title changed to reflect that.

Also, yes.

sudo apt-get remove --purge $package

where $package is what you want to get rid of.

---

### Post by molex on 2007-01-31
```
Molex@BlackMonster:~$ sudo apt-get remove --purge virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  airstrike-common virtualbox airstrike
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  airstrike virtualbox*
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 19.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 138854 files and directories currently installed.)
Removing airstrike ...
(Reading database ... 138854 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--purge):
 subprocess pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
Errors were encountered while processing:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)[

UGH

```

---

### Post by molex on 2007-01-31
GOT IT TO WORK

HAD to PS the process

---

### Post by Brunellus on 2007-01-31
> **molex said:**
> GOT IT TO WORK

HAD to PS the process
let me be the first to say

W00T!

---

### Post by miseljt on 2007-02-01
I'm also having that problem, but I can't purge it.

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

sudo apt-get remove --purge virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by miseljt on 2007-02-01
Nevermind, I just reinstalled Edgy. I didn't lose anything because I have my root folder and /home on different partitions. Thanks through.

---

### Post by pixatintes on 2007-02-03
I have the same  problem with .deb, hl1850pr (brother printer driver).

I found the solution:
edit the /var/lib/dpkg/status, and delete the package entry (in my case hl1850pr).

And it's all. It works for my.

Good luck.

---

### Post by Medieval_Creations on 2007-02-05
I was having the same problem when I installed the VirtualBox .deb.  even after apt-getting the associated packages.  I skimmed through the log VBox log file that is listed in the error and it's looking for a module file that is only created when you compile a new kernel.  Then I reinstalled the .deb file and it installed with no problems.

[i]*Note: you just have to compile it, you don't have to install the new kernel.  It won
t effect your current system to compile it.[/i]

---

