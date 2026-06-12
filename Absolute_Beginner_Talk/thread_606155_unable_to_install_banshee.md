---
title: "unable to install banshee"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by biddy on 2007-11-07
hello ubuntu community

i get the following error when I try to install banshee, i have added through synaptic but when is issue command in terminal get the following error.

warren@warren-desktop:~$ sudo apt-get install banshee
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
warren@warren-desktop:~$ 

i'm lost :(

---

### Post by Maestro23 on 2007-11-07
> **biddy said:**
> hello ubuntu community

i get the following error when I try to install banshee, i have added through synaptic but when is issue command in terminal get the following error.

warren@warren-desktop:~$ sudo apt-get install banshee
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
warren@warren-desktop:~$ 

i'm lost :(

If you installed thru Synaptic, why are you trying to install it thru command line. If it installed correctly, you should have an entry in your Apps menu.

---

### Post by taurus on 2007-11-07
And besides, you can't have synaptic running while you run "sudo apt-get" command.  If you want to use the terminal, you need to _close_ synaptic first.

---

