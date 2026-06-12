---
title: "network error??"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by paquito on 2006-03-12
Hi,

On boot into ubuntu before the login screen, I get the following message:

> "No servers were defined in the configuration file and XDMCP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration. Note that auto and timed logins are disabled now"

I have no idea what the configuration file is? And what is causing this message? I did not get this message before, but can't recall what settings were changed to cause this. Been a while since i've rebooted linux (the advantages of a stable OS), so not sure when this started. I had tried to set up samba a whie ago and this may have caused this. 

Any help would be appreciated

---

### Post by encompass on 2006-03-12
your xdmcp setting can be found in System Administration and login screen.  make sure that they are off and not in use.  As you don'e know what it is I wouldn't have it on.  That may clean up the old confige file.  Hope that helps.:D

---

### Post by soonindallas on 2006-03-12
try System > Admin > Login Window >'security' tab > click on configure X server

---

### Post by u-blunt-2 on 2006-06-04
I had the same error message when starting GDM and I think it was caused by some messing around with SAMBA packages. Try this :
```
sudo gedit /etc/gdm/gdm.conf
```
```
...
[xdmcp]
Enable=0
...
[servers]
0=usr/bin/X11/X

```

Worked for me !

---

