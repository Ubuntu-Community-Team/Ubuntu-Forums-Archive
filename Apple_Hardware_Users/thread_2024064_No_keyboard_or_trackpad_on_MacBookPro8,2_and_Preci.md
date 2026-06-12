---
title: "No keyboard or trackpad on MacBookPro8,2 and Precise 12.04 - Please help!"
date: 2012-07-13
forum: Apple Hardware Users
---

### Post by petersphilo on 2012-07-13
Hello all,

i'm sorry to bother everyone with this, but i cannot manage to fix this...

Background:
A while back, i installed Ubuntu 12.04 on a MacBook Pro 5,2, and everything was working great (multi-boot with: OS X 10.6.8; ubuntu; and Win7).

i recently bought a MacBook Pro 8,3 and, for many many reasons, i wanted the same setup, so i switched the hard drives and used the ones from the MacBookPro 5,2 (i have the OWC diskdoubler)

everything works perfectly, except that i cannot get Ubuntu to recognize the keyboard or the trackpad. 
Note: i may have tried to run Ubuntu in Parallels, so i'm not so sure if it's the switch of MacBook Pro's or using Parallels that is the cause...

EDIT: i don't think i ever used this as a Parallels VM, so forget about the Parallels stuff... Sorry

EDIT: Does anyone know any tricks to reinstall keyboard and trackpad drivers other than the methods tried below, or even just how to force Ubuntu to rescan its configuration?


i've tried everything i could think of like:

i read [here]("http://www.yaleman.org/2012/01/12/keyboard-issues-on-macbook-and-pro-with-ubuntu-and-vmware-fusion/") that i should do this:
dpkg-reconfigure console-setup

but it never mentioned the keyboard anywhere, even if i hit the M key


i tried reinstalling the x-org input as seen [here]("http://www.ehow.com/how_6800109_reinstall-ubuntu-using-command-line.html"):

sudo apt-get remove --purge xserver-xorg
sudo apt-get remove --purge xserver-xorg-input-all
sudo apt-get remove --purge xserver-xorg-input-synaptics

sudo apt-get install xserver-xorg
sudo apt-get install xserver-xorg-input-all
sudo apt-get install xserver-xorg-input-synaptics


Then i tried these steps, mentioned [here]("http://www.ubuntubuzz.com/2011/06/install-ubuntu-1104-on-macbook-pro-81.html"):

sudo apt-get install bcm5974-dkms xserver-xorg-input-synaptics
sudo apt-get install xf86-input-multitouch bcm5974-dkms

setting the trackpad, edit xorg.conf (/etc/X11/xorg.conf), add following line in the end of xorg.conf file :
   Section "InputClass"
            MatchIsTouchpad "true"
            Identifier "Multitouch Touchpad"
            Driver "multitouch"
     MatchDevicePath "/dev/input/event*"
     EndSection


I also tried, as mentioned [here]("http://ubuntuforums.org/showthread.php?t=1155020") changing the **/etc/modules** file to add the following:
bcm5974
usbhid

---

### Post by petersphilo on 2012-07-17
i'm sorry, i made a small mistake, my new MacBook Pro is actually 8,3 rather than 8,2 -- i was just used to the 17-inch model ending with a 2 because of the 5,2 i had before....


Please, if anyone has any suggestion on this issue, i'd really love to hear it!

i've read somewhere that maybe 'blacklisting' the bcm5974 driver could help...


it seems like Ubuntu Precise simply sees neither the keyboard nor the trackpad..

---

### Post by BDNiner on 2012-07-17
I also have a similar problem. I run ubuntu in Parallels on my mac. When I updated to the latest version the magic mouse no longer works inside the VM. I can use the keyboard fine. I was able to reinstall Parallels Tools software but still nothing.

---

### Post by Lunarts on 2012-07-25
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825)

---

