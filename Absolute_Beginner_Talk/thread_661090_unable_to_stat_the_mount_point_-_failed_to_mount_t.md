---
title: "unable to stat the mount point - failed to mount the cdrom"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by goodhope on 2008-01-07
hello all,

after hours i got ubunto minimal installation installed. then i wanted to install vmware workstation 6 which took me also some hours but it didin't finish because of the error:

The following libraries could not be found on your system: 
libX11.so.6 
libXtst.so.6 
libXext.so.6 
libXrender.so.1 

after some hours using google i found out that i need to install the essential package. i googled again a lot but didn't get it to work. 

when i want to install the package it says "unable to stat the mount point /cdrom/ - stat (2 no such file or directory)

please can you help me to install vmware workstation or the missing essentials package?

---

### Post by Miademora on 2008-01-07
The stat error message suggests that its searching for packages on a cdrom with no cd inserted. You could insert the ubuntucd or change your repositoryconfig from apt-get to look somewhere else for the required packages.

---

### Post by goodhope on 2008-01-07
> **Miademora said:**
> The stat error message suggests that its searching for packages on a cdrom with no cd inserted. You could insert the ubuntucd or change your repositoryconfig from apt-get to look somewhere else for the required packages.

thanks for your reply,

i had the ubuntu alternate cd in the cdrom

i used apt-cdrom -d /media/cdrom0 add

---

### Post by spiderbatdad on 2008-01-07
build-essential is in the synaptic package manager

---

### Post by goodhope on 2008-01-07
> **spiderbatdad said:**
> build-essential is in the synaptic package manager

i started yesterday using linux so i hope its ok to ask this :-) what are you trying to tell me, did i do something wrong or do i have to do something?

---

### Post by goodhope on 2008-01-07
anyone can help, or do you suggest to install ubuntu in a normal version? i just need it for using vmware so i thought the lightweight minimal installation would be better.
please can someone tell me what to do?

---

### Post by goodhope on 2008-01-07
ok. last try. anyone can please help me?

---

### Post by spiderbatdad on 2008-01-07
you can navigate to synaptic package manager by clicking System>>Administration>>Synaptic Package Manager. then scroll to "Build-Essential" and check the box. If you do not have a working internet connection, you will be asked for the Ubuntu cd.

---

