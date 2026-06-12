---
title: "Error with sudo modprobe..."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by M0rThden on 2007-02-20
When i use sudo modprobe ndiswrapper it doesnt work. This is what i get when i plug it in terminal. Im trying to install my wireless card. It says driver installed, hardware present. This is what i get.

shatcher@shatcher-laptop:~$ ndiswrapper -l
Installed ndis drivers:
tmimo3p driver present, hardware present 
shatcher@shatcher-laptop:~$ sudo depmod -a
Password:
shatcher@shatcher-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
shatcher@shatcher-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

shatcher@shatcher-laptop:~$

---

### Post by RomeReactor on 2007-02-20
Hi. Did you install **ndiswrapper-utils**? If you're not sure, search for them on Synaptic; or from the terminal:

```
sudo apt-get install ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8
```

Then continue with modprobe.

---

### Post by M0rThden on 2007-02-20
Nope i dont recal doing that...let me try.

Thank you

---

### Post by M0rThden on 2007-02-20
I did that and when i tried it again it froze the GUI and i had to restart. I might check the ndiswrapper wiki again for that problem.x

update: When i put the card back in it freezes instantly. It seems that something went wrong between installing those other things and sudo modprobe.

---

### Post by RomeReactor on 2007-02-21
Is your card a Broadcom? To find out, type in the terminal

```
lspci | grep Ethernet
```

Maybe you need to delete the driver provided with Ubuntu (it might create conflict if you're using NdisWrapper); so, still in the terminal:

```
cd /lib/modules/**KERNEL_NAME**/kernel/drivers/net/wireless/bcm43xx
```

and

```
sudo rm bcm43xx.ko
```

where **KERNEL_NAME** is the kernel you are actually using now (probably the newer one). Note that every time you update your kernel you must delete the driver it installs. I think another way of doing this (though i don't remember correctly) is by blacklisting the driver:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and adding at the end

```
bcm43xx
```

Then reboot. See if that works.

---

### Post by M0rThden on 2007-02-21
shatcher@shatcher-laptop:~$ lspci | grep Ethernet
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
03:00.0 Ethernet controller: Airgo Networks Inc Unknown device 0002 (rev 01)
shatcher@shatcher-laptop:~$ 


So it appears i dont have a Broadcom card. Is that a problem?

---

### Post by funkadelic on 2007-02-21
I had a very similar problem -- try compiling ndiswrapper from source. That is what finally got things working for me.

ALSO: If this is a USB drive, try unplugging and re-plugging it before you modprobe ndiswrapper.

---

### Post by M0rThden on 2007-02-21
Its pci as far as laptops go. I have been doing everything with ndiswrapper in terminal. I might need to update to the newest version if i knew how lol.

---

### Post by M0rThden on 2007-02-21
Well it turns out that i looked a little closer at the driver list and mine is listed but for the 1.37 version. *sigh* now its trouble to figure out how to get it to install correctly

---

