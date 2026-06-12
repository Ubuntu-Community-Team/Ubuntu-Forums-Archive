---
title: "ubuntu server no wifi - broadcom BCM43224 (but worked during installer)"
date: 2016-06-11
forum: Apple Hardware Users
---

### Post by mp3sub on 2016-06-11
I have a working dual boot setup on my macbook air 5,2 with OSX Mavericks, Ubuntu 16.04 desktop.  Wireless works fine.

Now I installed Ubuntu 16.04 Server on another partition. During installation, WIFI was detected but after installation and when I boot into the server, wifi isn't detected.  

Here's the lspci output:

$ sudo lscpi -vv
02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

What is the best way to get WIFI working? I don't have a wired connection.
Can I copy and install the wifi drivers from the working 'ubuntu desktop' partition? 

Please help.

---

### Post by jeremy31 on 2016-06-11
Check the blacklist on the desktop ```
cat /etc/modprobe.d/blacklist.conf
``` and check what modules are loaded```
lsmod
```
Chili555's sticky in the Networking forums says that sometimes you need to blacklist the b43 and possibly ssb for the module to work

---

### Post by mp3sub on 2016-06-11
Thanks for the quick reply.

The blacklist.conf file is same on both my desktop partition and server partition (/dev/sda8).
$ sudo diff /etc/modprobe.d/blacklist.conf /mnt/sda8/etc/modprobe.d/blacklist.conf 


I have attached the lsmod output from my working desktop partition (when running in desktop ubuntu).

---

### Post by jeremy31 on 2016-06-11
The working desktop partition is using bcmwl-kernel-source as a module.  So you could just copy wl.ko as long as they use the same kernel or install with ```
sudo apt-get install bcmwl-kernel-source
```

This is a strange chipset as [https://wireless.wiki.kernel.org/en/users/drivers/b43](https://wireless.wiki.kernel.org/en/users/drivers/b43) shows that it is supported by b43(after installing firmware), bcmwl, and brcmsmac.  The only question would be what module works best and I doubt any of the three will allow you to use 2.4GHz over channel 11

---

### Post by mp3sub on 2016-06-11
What is the location of this file 'wl.ko' on my working desktop partition?  Yes both desktop & servers use the same kernel.

---

### Post by howefield on 2016-06-11
Moved to "*Apple Hardware Users*" forum.

---

### Post by jeremy31 on 2016-06-11
Use ```
locate wl.ko
``` and copy the one for the newest kernel

---

### Post by mp3sub on 2016-06-11
I copied wl.ko but no luck. 

$ sudo cp /mnt/sda6/lib/modules/4.4.0-21-generic/updates/dkms/wl.ko /lib/modules/4.4.0-21-generic/updates/dkms/.
$ sudo cp /mnt/sda6/lib/modules/4.4.0-21-generic/updates/dkms/wl.ko /lib/modules/4.4.0-21-generic/updates/.
$ sudo reboot

Since the installer in the USB stick is correctly detecting WIFI, is there a way to point 'apt' to use USB as one of the sources and install the drivers?

---

### Post by jeremy31 on 2016-06-11
I forgot one step as I was thinking about moving it to another area and howefield beat me to it
```
sudo depmod -a
```
Reboot and after that I would suggest running ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
``` in the server because that module is only good for the current kernel unless you want to copy it after every kernel update

---

### Post by mp3sub on 2016-06-11
no luck after running "sudo depmod -a" and rebooting. Perhaps I am not copying wl.ko to the right folder?  Where should the 'wl.ko' go so that 'depmod' picks it up?  Is there a way to confirm if it picked it up? Any logs I should look?

---

### Post by jeremy31 on 2016-06-11
Another issue may be the blacklist that bcmwl includes
```
echo "blacklist b43" sudo tee /etc/modprobe.d/blacklist-b43.conf
echo "blacklist ssb" sudo tee -a /etc/modprobe.d/blacklist-b43.conf
echo "blacklist bcma" sudo tee -a /etc/modprobe.d/blacklist-b43.conf
echo "blacklist brcmsmac" sudo tee -a /etc/modprobe.d/blacklist-b43.conf
echo "blacklist brcmfmac" sudo tee -a /etc/modprobe.d/blacklist-b43.conf
```
reboot

---

