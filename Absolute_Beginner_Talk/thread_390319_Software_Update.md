---
title: "Software Update"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-03-21
Hi:
I have uninstalled automatix2 using synaptic.  I have a software update for frostwire.  When I try to update it, software updater gives me this message:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/frostwire_4.13.1-6~edgy3_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/frostwire_4.13.1-6~edgy3_i386.deb)
  503 Service Temporarily Unavailable

I tried doing:

sudo aptitude --purge automatix2

But I still get the message.

What should I try?

Thanks,
Ziffnabb

---

### Post by kpkeerthi on 2007-03-21
getautomatix.com is currently down. Retry your update/uninstall process after a day or so.

---

### Post by teaker1s on 2007-03-21
The server is temporarily unable to service your request due to maintenance downtime or capacity problems. ...

---

### Post by azurehi on 2007-03-22
[QUOTE=ziffnabb;2334419]Hi:
I have uninstalled automatix2 using synaptic.  I have a software update for frostwire.  When I try to update it, software updater gives me this message:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/frostwire_4.13.1-6~edgy3_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/frostwire_4.13.1-6~edgy3_i386.deb)
  503 Service Temporarily Unavailable

Having the same problem...but today I get the following message after trying to update frostwire:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.   I'm unsure what to type in a terminal.  Or, should I just wait for automatix to be back up?  Thanks :confused:

---

### Post by teaker1s on 2007-03-22
terminal type
```
sudo dpkg --configure -a
```
what has happened is-package has been interupted and until situation is rectified you can't install or update anything

---

