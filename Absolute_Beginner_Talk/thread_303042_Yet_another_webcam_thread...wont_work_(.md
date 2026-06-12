---
title: "Yet another webcam thread...wont work :("
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by blackangst on 2006-11-19
Hi everyone :) Long time lurker, new linux user, first time poster :D OK my stats first:

Edgy Eft
AMD64 3200
MSI mobo
Nvidia 6800 vid card

OK. Now, I did a search, and literally follow every direction in every thread I could find (took 3 days lol)I've tried several re-installs (no check-sum errors on my disk, BTW). I've tried deleteing all files before try a new install of drivers. The errors I am getting are: In Camorama-Could not connect to video device (/dev/video0). Please check connection. In Kopete: a blue screen.

I have tried unplugging and re-plugging, as well as using other USB ports. Here is the output of what I think you might need:

dan@dan-desktop:~$ lsusb
Bus 001 Device 003: ID 046d:08a2 Logitech, Inc. Labtec WebCam Pro

dan@dan-desktop:~$ sudo modprobe spca5xx
(no results)

dan@dan-desktop:~$ ls /dev/video*
/dev/video  /dev/video0

Tried sudo ln -s /dev/video /dev/video0 both ways, same error.

dan@dan-desktop:~$ sudo apt-get install gqcam
----SNIP INSTALL STUFF----
Setting up gqcam (0.9.1-3) ...

dan@dan-desktop:~$ sudo ln -s /dev/video0 /dev/video
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
dan@dan-desktop:~$ gqcam
/dev/video: No space left on device

dan@dan-desktop:~$ lsmod | grep spca5xx
spca5xx               680016  0 
videodev               10752  1 spca5xx
usbcore               134912  8 spca5xx,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd

dan@dan-desktop:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
linux-restricted-modules-2.6.17-10-generic is already the newest version.
build-essential is already the newest version.
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

dan@dan-desktop:~$ su
Password: 
root@dan-desktop:/home/dan# CC=gcc-3.4
root@dan-desktop:/home/dan# export CC
root@dan-desktop:/home/dan# exit
exit
dan@dan-desktop:~$ CC=gcc-3.4
dan@dan-desktop:~$ export CC
dan@dan-desktop:~$ cd spca5xx-20050906
bash: cd: spca5xx-20050906: No such file or directory
dan@dan-desktop:~$ make clean
make: *** No rule to make target `clean'.  Stop.

dan@dan-desktop:~$  ls /dev/ | grep video
video
video0
dan@dan-desktop:~$ 


OK Im not sure what else you might need....suggestions? 

P.S. My cam *is* on the supported list :p

---

### Post by blackangst on 2006-11-21
/bump

Anyone?

---

