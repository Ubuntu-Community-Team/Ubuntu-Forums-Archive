---
title: "Lockdown ubuntu?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by yeleek on 2007-04-16
So new to Ubuntu, primarily with the plan of running a vm in the background on a xp box to provide dansguardian, etc.

Simple enough question, what if any software (firewall/av/etc) should i run on ubuntu.  Obviously coming from MS, am use to having to lockdown the services/perms/etc.  Whats best practice to do on Ubuntu for a beginner?

Thanks

---

### Post by justleen on 2007-04-16
a new install is already pretty safe, by default.
 

If you want a nice firewall tool, look into [firestarter]("http://www.fs-security.com/"). 
as for AV..  im pretty sure there must be some AV tool for linux.. most vurnabilties get fixed really fast, so there is practicly no virusses on linux..

---

### Post by 3rdalbum on 2007-04-16
So, let me get this straight: You'll be running Ubuntu inside a virtual machine. The virtualisation software is running on a Windows host.

If that's correct, then you should do whatever necessary to lock down the Windows side. The default Ubuntu install is very secure already (doesn't listen on any ports), so I'd be more concerned about security on the Windows part.

If you install Ubuntu Server, you should probably make sure that it doesn't install the LAMP stack (Apache, MySql and PHP). If it does, you can remove them by the following commands:

```

sudo apt-get remove --purge apache2-*
sudo apt-get remove --purge mysql-*
sudo apt-get remove --purge php*

```

---

### Post by yeleek on 2007-04-16
Yep ubuntu in a vm (bridged networking) on XP.  

Windows is sufficiently locked down (well as much as poss), but as Ubuntu is using bridged networking just wondered what had to be done from that point of view.  Using Ubuntu desktop so no lamp.

Thanks

---

