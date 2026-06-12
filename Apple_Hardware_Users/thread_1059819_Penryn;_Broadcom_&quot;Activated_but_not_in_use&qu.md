---
title: "Penryn; Broadcom &quot;Activated but not in use&quot;"
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by MaddMatt on 2009-02-04
Hi All; 

I've been flopping between ndiswrapper and broadcom due to the freezes that the broadcom driver caused with previous kernels. Now that I'm on 2.6.27-11 I decided to give it another shot, but nothin' doing:

'Hardware drivers' Reports that the driver is "activated but not currently in use". 

lsmod doesn't list a 'wl' driver, however it does list bcm drivers:
```
~$ lsmod |grep bcm
bcm5974                17152  0 
usbcore               175888  8 bcm5974,uvcvideo,appleir,btusb,usbhid,ehci_hcd,uhci_hcd

```

I tried removing the bcm drivers with modprobe and it disabled my trackpad, so not the right thing to do. ha!

Anyway, trying to manually add the 'wl' driver to modprobe gives me this error:
```
$ sudo modprobe -a wl
FATAL: Error inserting wl (/lib/modules/2.6.27-11-generic/volatile/wl.ko): Invalid module format
WARNING: Error running install command for wl

```

So I'm kind of stymied. 
Any ideas?


Here are some more outputs. 

```
~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

Also on a somewhat related note, ndiswrapper stopped working too- is the bcmwl5.inf correct for 64-bit as well?

Thanks for the help, 
m

---

### Post by cyberdork33 on 2009-02-04
well it would make sense since the bcm5974 driver is your trackpad driver :)

the open broadcom drivers are:
b43
b43-legacy
bcm43xx

Did you ever compile the wl driver yourself or with a script? Maybe if you remove it from the hard ware drivers dialog and then add it back again. (otherwise reinstall from the commandline, but I am not sure of the package name.)

for ndiswrapper and 64 bit, you have to use the 64bit windows driver. The 32bit and 64bit versions of the same driver are usually included in the same bundle. I can't remember if there is a separate inf file for the 64bit as it has been so long since I have used ndiswrapper.

---

### Post by Phis on 2009-06-04
this is what i did to get it working, i shut off my card manually, the activation button on the side of my laptop. Then I went to hardware driver menu and desactivated and re-activated the driver. restarted. started the wireless card.

---

### Post by cyberdork33 on 2009-06-04
> **Phis said:**
> this is what i did to get it working, i shut off my card manually, the activation button on the side of my laptop. Then I went to hardware driver menu and desactivated and re-activated the driver. restarted. started the wireless card.
Macs don't have a hardware button like that, but I have heard that you can disable the driver, reboot, and reenable (and reboot again) and it should work.

---

### Post by Matt3223 on 2009-08-16
> **cyberdork33 said:**
> Macs don't have a hardware button like that, but I have heard that you can disable the driver, reboot, and reenable (and reboot again) and it should work.

Just got Jaunty installed on my early 2008 MacBook....had this exact problem and this sequence worked like a charm!

Thanks cyberdork!!

---

