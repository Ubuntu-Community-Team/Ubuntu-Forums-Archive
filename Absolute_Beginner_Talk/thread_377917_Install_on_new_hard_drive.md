---
title: "Install on new hard drive"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-06
I want to try ubuntu for the first time and install on a new unformatted hard drive. Everything I seem to read is about installing on a system with windows already running. Can I install on a new drive and should I use the desktop CD or the alternate CD. I have an AMD 64 bit dual core CPU and want to install the AMD 64 bit version.

---

### Post by bulldog on 2007-03-06
Both are good to use,the only difference is the graphical interface with the live cd.
A warning though,if you have no experience with ubuntu,it's maybe better to run the 32bits version.
It's some what harder to get things working in a 64bit environment.

That said,it could be a wise thing to manually partition your drive when you come to the partitioner.

My recommendation should be:
Make a /  (root) partition of 10GB and format it as ext3
Make a swap file 1GB and format it as  swap
Make a /home as big as you like,for your data,it might even be the rest of your available space,and format it as ext3.

Mount those partition as /,swap and /home and you can accomplish the install.

You don't need windows to be installed,just boot from your cd and choose start or install.
The rest is self explaining.

---

### Post by D10 on 2007-03-06
Yes you can install it on a new drive.

As the desktop vs alternate CD goes, it really doesn't matter. The desktop runs a live CD version and you click an icon to install it. The alternate is a text based installer.

Both are easy to setup the desktop a little more so. Some have had problems with the desktop versions, but I never have.

If this is your first time with linux I personally would recommend using the 32bit CD and not the 64 bit. Not everything works well in the 64 bit version.

---

### Post by OldDog11 on 2007-03-06
Thanks for your help, it's appreciated.

---

