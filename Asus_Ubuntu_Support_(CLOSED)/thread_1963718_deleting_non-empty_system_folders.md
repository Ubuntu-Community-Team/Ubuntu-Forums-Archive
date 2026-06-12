---
title: "deleting non-empty system folders"
date: 2012-04-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by halfhearted on 2012-04-22
I'm using an Asus EEEPC 901 which has very limited RAM in the file system. I would like to delete some old linux header folders from usr/src. I keep getting warnings that the computer only has 139MB of memory left. The directory usr/src contains -
linux-headers-3.0.0-12-generic  
linux-headers-3.0.0-15          
linux-headers-3.0.0-15-generic  
linux-headers-3.0.0-16
linux-headers-3.0.0-16-generic
linux-headers-3.0.0-17
linux-headers-3.0.0-17-generic
I would like to delete everything but the most recent linux headers (ie. 17) which I am currently using. The system prevents me from doing this. I have been trying to do this from a terminal for days and I simply cannot do it. There MUST be a straightforward way. Any help appreciated.

---

### Post by papibe on 2012-04-22
Hi halfhearted.

You can use synaptic to remove/uninstall old kernels. It would be a good idea to keep at least one old, though.

Check this [article ]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/")(video included) for the details on how to do it.

Regards.

---

### Post by halfhearted on 2012-04-23
papibe I am using Ubuntu 11.10 which doesn't come with Synaptic and I haven't got room to install it anyway. I need to free up space rather than installing yet more stuff. Any ideas on how to get rid of old kernels from usr/src where I am denied permission  would be greatly received. Thanks.

---

### Post by papibe on 2012-04-23
Then I would take this emergency steps:

First take note of your actual space usage:
```
df -h
```
Then clean as much as possible using apt-get:
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
And finally, check again your free space (df -h) to see if you have enough to install synaptic.

Tell us how it goes.
Regards.

---

### Post by halfhearted on 2012-04-23
Thanks for the suggestions. I have seen "clean" and "autoclean" before but not "autoremove" or "df -h", I finally got rid of them by doing this -
1) open terminal
2) navigate to usr/src
3) run "sudo rm -rf nameofdirectory" (where nameofdirectory=old linux)
4) that did it

Thanks for your time.

---

