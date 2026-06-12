---
title: "acpi error"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-04-20
what would cause this?

 Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
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
 acpi-support
 powermanagement-interface
E: Sub-process /usr/bin/dpkg returned an error code (1)
tasksel: aptitude failed (100)

---

### Post by Diabolis on 2008-04-21
Well its telling you that your acpi installation is either an older version than what is required, the installation is broken or is not well configured.

Maybe a:
sudo apt-get update
sudo apt-get upgrade

could fix it.

Check for broken packages:
system / synaptic package manager / edit / fix broken packages

And don't forget to check if its not installed, you can do it at synaptic too.

---

