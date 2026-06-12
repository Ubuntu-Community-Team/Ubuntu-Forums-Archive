---
title: "'Partial Upgrade warnings"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Goop on 2008-03-01
Hey everyone,

I've been having some problems with Package Manager and apt-get. I installed Apache a while ago and didn't use it, so I used the command:
```
sudo apt-get remove apache2
```
-to get rid of it. I did the same for the MySQL package (I can't remember the name right now). But when I next opened Package Manager, I got a warning about running a partial upgrade, being due to something not being removed properly. But when I do, the bar fills up with a 'Reading cache' subtitle, then closes the window as well as Package Manager.

When I try to install or remove anything via Terminal, I get this error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
matt@matt-desktop:~$ 
```
When I run that command (as superuser), this is the output I get:
```
matt@matt-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
matt@matt-desktop:~$ 
```
Now I'm no Linux expert, but I think something has gone wrong when trying to update the kernel. I've checked to see if **initrd.img-2.6.22-14-generic** is there, and it is, along with a backup of it.
I cannot update anything else through the Terminal or Package Manager; I get the same error message listed first. I'm using Ubuntu 7.10. Any help is greatly appreciated.

---

### Post by SOULRiDER on 2008-03-01
Try:
```
sudo aptitude update
sudo aptitude install util-linux
```
Finally try
```
sudo aptitude dist-upgrade
sudo dpkg --configure -a
```

---

### Post by fissionmailed on 2008-03-02
I've been having the same problems.  It all started with me after I updated the headers. :\

---

### Post by fissionmailed on 2008-03-02
I got mine working that was like that.
[http://ph.ubuntuforums.com/showthread.php?t=706871](http://ph.ubuntuforums.com/showthread.php?t=706871)
Is the thread that got it to work.

The basic steps are 
1. Download the right util-linux from here [http://packages.ubuntu.com/gutsy/util-linux](http://packages.ubuntu.com/gutsy/util-linux)
2. Once you get the file, extract it, and go to and extract the data file.
3. Go to the urs and then the bin and get the getopt file.
4. I copied it into the urs sbin and bin folders but I'm not sure if you need both but I was like I"ll try everything thing haha.
5. Assuming you're in the directory with the getopt file
```
sudo cp getopt /usr/sbin
sudo cp getopt /usr/bin
```
6. Then I configured the dpkg like
```
sudo dpkg --configure -a
```
7. Installed util-linux like
```
sudo apt-get install util-linux
```
8. I restarted and all was well.  

I hope this helped.

---

