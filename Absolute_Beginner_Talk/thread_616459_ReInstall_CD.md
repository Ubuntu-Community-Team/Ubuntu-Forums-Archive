---
title: "ReInstall CD"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by jbguev on 2007-11-18
Is it possible to create an installation/live CD from my current system configuration?  Since I seem to make progress in Ubuntu and then totally screw something up and need to reinstall the OS, I would love to just burn a new installation CD with all my current settings so that I don't have to reconfigure everything from scratch.

Thanks,

Jerry

---

### Post by kiepmad on 2007-11-18
This are the only possibilities I can think of, but I am not sure if they can provide for what you need.
Just have a look at them:
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by nick_h on 2007-11-18
You may be better to just create a [separate home partition](http://psychocats.net/ubuntu/separatehome).

Also, have a look at [APTonCD](http://aptoncd.sourceforge.net/) to make a backup of the packages you have installed.

You will probably also have to restore some files in your /etc directory as well.

---

### Post by gazzadtfan on 2007-11-18
Hi

it sounds like you don't have a separate partition for your /home. If you make a separate partition for this then reinstalling the OS shouldn't make any differences to your old settings. 

try this site for further help. 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

gazzadtfan

---

### Post by Sbarton on 2007-11-18
Having a Home Partition is beneficial as you can save all your documents etc.
As for the rest of your settings inc. progs I am not sure what you will need!
maybe a disc clone would suit your needs. To be honest I have changed /upgraded a couple of times and it does not take long to get back to where you were interms of settings and progs.
regards

---

### Post by jbguev on 2007-11-18
Thanks for all the advice.  Can I save things like bookmarks and program configurations in my home directory?

Jerry

---

### Post by nhandler on 2007-11-18
I know firefox stores its bookmarks in the home folder. Various other programs also store configuration data there. These files are in hidden folders that have names that start with a "."

---

### Post by nick_h on 2007-11-19
> **jbguev said:**
> Can I save things like bookmarks and program configurations in my home directory?

All user program settings are stored in the home directory.  These include bookmarks, emails, preferences etc...

Settings stored in /etc are system-wide and you will probably know if you have changed anything in there.  For example, you may have made changes to /etc/X11/xorg.conf for specific video requirements.  You may have changed /etc/default/acpi-support to customise suspend or hibernate.  Network settings can be changed in /etc/network/interfaces, modules loaded or blacklisted in /etc/modules and /etc/modprobe.d/blacklist.

You may not have configured anything in /etc though.

---

