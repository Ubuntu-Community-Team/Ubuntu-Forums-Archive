---
title: "vmware: error connecting to localhost"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by lgastmans on 2007-11-09
Hi All,

I have installed VMWare on my machine, but when I try to connect to "Local host" i get the following error:

The local VMware Server is not installed, or is not currently running.
Make sure that the server is properly installed and try again.

What happened is that I installed VMWare, then realized I was booting with an older kernel version, booted with the latest kernel. So when executing the following command :

sudo ./vmware-install.pl

I got the following message somewhere along the line:

Your kernel was built with "gcc" version "4.1.2", while you are trying to use 
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.3" anyway? [no] yes

I answered yes, because when I answered no before it just stopped the installation process.

Help much appreciated

---

### Post by Dripbagulhos on 2007-11-09
Hi

Sorry if you already did it, but I think it is worth to try. Have you installed xinetd?

I think the problem is not the version of your C compilator. I think the xinetd is the point...

You can install it by doing:

```
sudo apt-get install xinetd

```

But I think it is better to follow this (very good) tutorial:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by lgastmans on 2007-11-09
yes, I installed xinetd. I found that at a good tutorial here at the forums.

Will now have a look at your link, and let you know

In the meantime, thanks for the help!

---

