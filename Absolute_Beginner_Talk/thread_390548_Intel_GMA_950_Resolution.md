---
title: "Intel GMA 950 Resolution"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Crafall on 2007-03-22
Just a note that I am completely new to Ubuntu and basically anything about it. So if this messes up your install, use at your own risk.
Well after some searching I was able to find a method that worked on my computer, Gateway MT6821.

[http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/](http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/)

In short
Download the i945GM driver from :

[http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm](http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm)

Go to the folder where u put the rpm file then do the alien. Usually a command like
cd /home/USER/Desktop/
*note* you must have the alien program or whatever. I just used the download all down towards the bottom.
[http://packages.debian.org/unstable/admin/alien](http://packages.debian.org/unstable/admin/alien)

Open up your terminal then:
sudo alien dri-Intel-3.4.3006-20051209.i386.rpm

Then:
sudo dpkg -i dri-Intel-3.4.3006-20051209.i386.deb

After that just reboot.

Just getting this out there if it helps anyone, if it was posted before feel free to just disregard this post.

---

