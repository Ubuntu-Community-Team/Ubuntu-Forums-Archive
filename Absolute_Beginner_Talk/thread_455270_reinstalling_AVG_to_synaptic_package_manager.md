---
title: "reinstalling AVG to synaptic package manager"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by redsox37 on 2007-05-26
I deleted AVG,

with this command
sudo dpkg -R -P avg75fld

 but didnt realize it would also remove it from synaptic package manager.

How can I get AVG back on synaptic package manager?

thanks

---

### Post by Happy_Man on 2007-05-26
From the dpkg man page:

> dpkg -r | --remove | -P | --purge package 
              Remove an installed package. -r or  --remove  remove  everything
              except configuration files. This may avoid having to reconfigure
              the package if it is reinstalled later. (Configuration files are
              the  files  listed  in the debian/conffiles control file). -P or
              --purge removes everything, including configuration files

You may need to run ```
sudo apt-get update
``` to fix it, though I'm not sure that will work....

---

### Post by mikewhatever on 2007-05-27
> **redsox37 said:**
> I deleted AVG,

with this command
sudo dpkg -R -P avg75fld

 but didnt realize it would also remove it from synaptic package manager.

How can I get AVG back on synaptic package manager?

thanks

Why do you need it in Synaptic? You can reinstall it any time from the downloaded deb file. It is probably possible to add AVG deb download location as a repository to the sources list, but again, why bother.

---

