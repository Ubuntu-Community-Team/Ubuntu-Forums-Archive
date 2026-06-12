---
title: "synaptic manager error message..."
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by tomasvestin on 2008-02-27
I'm an absolute newbie on Ubuntu but nevertheless I've installed the game Neverwinter Nights from instructions via the terminal and also installed new graphics driver but now I've got error messages in a couple of programs.
Neverwinter Nights work just fine but Amarok says xine doesn't work for example and synaptic package manager says things like:
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

What have I done and howto fix it??
/Tomas

---

### Post by dca on 2008-02-27
Go back into Synaptic and click on the 'custom filter' button on bottom left, then click on 'Broken' option and see if it lists anything.
 
Under the 'edit' on menu there should be a 'fix broken packages' option also...

---

### Post by jan quark on 2008-02-27
try also this terminal command

```
sudo dpkg --configure -a
```

---

### Post by tomasvestin on 2008-02-27
I did the "Broken" search and came up with nothing also tried to fix broken packages and still nothing :(

Well, the terminal command looks like follows:

tomas@Vestin-1:~$ sudo dpkg --configure -a
[sudo] password for tomas:
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 ubuntu-desktop
 acpi-support
 powermanagement-interface
tomas@Vestin-1:~$

---

### Post by tomasvestin on 2008-02-27
Well, Amarok works now anyway :)
Thanks!

---

