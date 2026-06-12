---
title: "How to install Gnome or KDE on  a Red Hat Enterprise Linux Server release 6.0?"
date: 2012-05-22
forum: Any Other OS
---

### Post by legolas_w on 2012-05-22
How to install Gnome or KDE on  a Red Hat Enterprise Linux Server release 6.0 (Santiago) from command line?

I tried commands like:

```

sudo yum groupinstall "Desktop" "Desktop Platform"
sudo yum -y groupinstall gnome

```

And the result was as shown below:

> 
Loaded plugins: aliases, changelog, downloadonly, kabi, presto, protect-packages, refresh-packagekit,
              : rhnplugin, security, tmprepo, verify, versionlock
This system is not registered with ULN.
ULN support will be disabled.
Loading support for kernel ABI
Setting up Group Process
Warning: Group Desktop does not exist.
Warning: Group Desktop Platform does not exist.
No packages in any requested group available to install or update



any idea what need to be done to fix it?

Thanks.

---

### Post by mutap on 2012-05-22
[FONT=monospace]http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/sn-switching-to-gui-login.html

[/FONT]But I am not sure if you can install it if you don't have licence and payed support. :confused:

On CentOS - yum groupinstall 'GNOME Desktop Environment' 'X Window System'

Try - yum grouplist | grep -i desk (or GNOME or KDE...)
To see what's available.

Other way should be installation from DVD media if it is listed as repository.

---

### Post by wojox on 2012-05-22
What repositories are you using?

---

### Post by BBQdave on 2012-05-22
> **legolas_w said:**
> How to install Gnome or KDE on  a Red Hat Enterprise Linux Server release 6.0 (Santiago) from command line?

RHEL offers Server and Desktop editions (among other products). To my understanding, RHEL Server is geared as the name implies, may not be the best workstation system.

You may want to give [Scientific Linux 6.2]("https://www.scientificlinux.org/") a try. It's DE is Gnome 2, but uses a combination of Gnome and KDE applications. And SL6 is RHEL 6: *the base SL distribution is basically Enterprise Linux, recompiled from source.*

---

