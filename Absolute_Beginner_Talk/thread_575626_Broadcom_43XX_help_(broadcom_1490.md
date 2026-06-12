---
title: "Broadcom 43XX help (broadcom 1490"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by dugh on 2007-10-14
I have a dell d820, 1490 wireless card (broadcom 4318, bcm4312).

In feisty I used these instructions to get wireless working, and had no problems:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
It involves compiling ndiswrapper and installing the dell drivers.

Now in Gutsy, Ubuntu installed its own restricted driver (bcm43xx i think) and a remote wl_apsta.o file.  The wireless was always failing, very unreliable.

So I disabled that and installed ndiswrapper again, but it still sometimes will not work.  It seems also like it will always fail if the computer is left alone for a while.  Perhaps I need to take it off laptop mode, although I had it in laptop mode in feisty, too. 

I've uninstalled/re-compiled/re-installed ndiswrapper often to no avail.

Anyone get a 1490 wireless card working reliably in Gutsy?  I'm going to have to downgrade back to Feisty.

---

### Post by dugh on 2007-10-14
Restarting the network on the command line seems to work when things go bad:

sudo /etc/dbus-1/event.d/25NetworkManager restart
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo dhclient eth1

Also this might possibly fix suspend/hibernate issues:

sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
sudo apt-get install splashy splashy-themes

#test suspend
#sudo s2disk

##to restore pmi for hibernation
## sudo dpkg-divert --rename --remove /usr/sbin/pmi

#if usb doesn't work on resume:
sudo rmmod uhci_hcd ehci_hcd
sudo modprobe uhci_hcd ehci_hcd

---

