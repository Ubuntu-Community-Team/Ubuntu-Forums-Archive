---
title: "Help with Files"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by dcj65 on 2007-01-28
I am very new to Linux, and I have installed Ubuntu 6.10 to a dual boot laptop. My problem is I tried to follow the directions on getting my Netgear wg111 wireless to work (unsuccessfully I might add) seems I might have a v1 instead of v2 that is stated on the side. My real problem is I'm not sure what I did but when I try to blacklist something and save it is says there no such file or directory....... I'm not sure were I went wrong but any help would be appreciated.

Ken

---

### Post by MkfIbK7a on 2007-01-28
what are the exact commands you put in?

---

### Post by dcj65 on 2007-01-28
I followed the instructions from the link below, which I found on this forum.


[http://ubuntuforums.org/showthread.php?t=212365](http://ubuntuforums.org/showthread.php?t=212365)

---

### Post by MkfIbK7a on 2007-01-28
ok what happens when you enter this?

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by dcj65 on 2007-01-28
i get one line in the terminal window that says

blacklist bcm43xx

---

### Post by MkfIbK7a on 2007-01-28
so it was blacklisted

---

### Post by dcj65 on 2007-01-28
So should I try the whole procedure again to get the wireless adapter working and if so should I be resetting anything before I do it?

---

### Post by MkfIbK7a on 2007-01-28
yes do the procedure again 
no dont reset anything this time

post any errors you get

---

### Post by dcj65 on 2007-01-28
This is what I get when I try to get it to work

ken@ken-laptop:~$ sudo ndiswrapper -m
WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 29: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 30: ignoring bad line starting with 'cd'
WARNING: /etc/modprobe.d/blacklist line 31: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 32: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 33: ignoring bad line starting with 'cd'
WARNING: /etc/modprobe.d/blacklist line 34: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 35: ignoring bad line starting with 'cd'
WARNING: /etc/modprobe.d/blacklist line 36: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 37: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 38: ignoring bad line starting with 'sudo'
modprobe config already contains alias directive

---

### Post by MkfIbK7a on 2007-01-28
ok do 

cat /etc/modprode.d/blacklist

post the output

---

### Post by dcj65 on 2007-01-28
This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

sudo rmmod bcm43xx
sudo rmmod ndiswrapper
cd to /lib/modules/kernel[6.10]/kernel/drivers/net/wireless
sudo mv acx /root/
sudo depmod -a
cd ~/desktop
sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_1386.deb
cd ~/desktop/xp
sudo ndiswrapper -i1.8-0ubuntu2.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
blacklist bcm43xx
blacklist bcm43xx
#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
blacklist bcm43xx
ken@ken-laptop:~$

---

### Post by MkfIbK7a on 2007-01-28
ok do this

sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist_backup

this backs up the file

all lines that say sudo in front of them remove the sudo

This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

sudo rmmod bcm43xx
sudo rmmod ndiswrapper
cd to /lib/modules/kernel[6.10]/kernel/drivers/net/wireless
sudo mv acx /root/
sudo depmod -a
cd ~/desktop
sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_1386.deb
cd ~/desktop/xp
sudo ndiswrapper -i1.8-0ubuntu2.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
blacklist bcm43xx[COLOR="Red"]~remove this line[/COLOR]
blacklist bcm43xx
#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
blacklist bcm43xx[COLOR="Red"]~remove this line[/COLOR]

that should do

see if that helps

---

### Post by dcj65 on 2007-01-28
I did everything you advised me to do and it still doesn't see the wg111 usb ,   could I have the wrong driver for the card.... and if it is do i just add another driver or do you have to go through everything all over again?


P.S. Thank you so much for everything up to this point

---

### Post by MkfIbK7a on 2007-01-28
try to add a new driver if that doesnt work than try redoing it

---

