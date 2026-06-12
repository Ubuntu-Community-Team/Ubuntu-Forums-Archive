---
title: "I cant get wireless connection"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Dahiasj on 2008-03-08
i cannot get Wireless connection to show in the network connection. 
i have a Broadcom BCM4328 802.11a/b/g/n Network card on my laptop if that helps. 
im new to this so please make it simple :D

---

### Post by ghost_ryder35 on 2008-03-08
**TWO**options and may I recommend the NDISwrapper way (seems that with the new "BCM4328" is having problems working with the BCM43xx module that is included in the new linux kernels.  Probally something to do with the draft N capabilities):
NDISWRAPPER and use windows drivers
Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper


4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi )
"

**[SIZE="7"]-OR-[/SIZE]**


1. **sudo apt-get install bcm43xx-fwcutter**
2. **sudo modprobe bcm43xx**
3. Shutdown and wait 60 seconds, then restart :)

---

### Post by radioaktivstorm on 2008-03-08
BCM 43** series can be a bit of a nightmare :/

if you do plan to use ndiswrapper, ndiswrapper-gtk is a nice little utility you can pull from the repositories to help you install the driver.  I havent done it in a while, so you may have to poke around for the rest of the steps, the instructions above look quite good  but it should let you install and use the windows driver :)

---

### Post by anewguy on 2008-03-08
> **ghost_ryder35 said:**
> **TWO**options and may I recommend the NDISwrapper way (seems that with the new "BCM4328" is having problems working with the BCM43xx module that is included in the new linux kernels.  Probally something to do with the draft N capabilities):
NDISWRAPPER and use windows drivers
Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper


4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi )
"

**[SIZE="7"]-OR-[/SIZE]**


1. **sudo apt-get install bcm43xx-fwcutter**
2. **sudo modprobe bcm43xx**
3. Shutdown and wait 60 seconds, then restart :)


You forgot one thing - you MUST blacklist the existing bcm43xx driver:

cd /etc/modprobe.d

sudo gedit blacklist

add the following line to the end of the file:

blacklist bcm43xx

save and exit, then REBOOT (this is a must).

:)

---

