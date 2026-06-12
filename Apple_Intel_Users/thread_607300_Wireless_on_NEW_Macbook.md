---
title: "Wireless on NEW Macbook"
date: 2007-11-08
forum: Apple Intel Users
---

### Post by addicted44 on 2007-11-08
I bought the latest Macbook (with X3100, base 2GHz model).  I have not been able to get the wireless on it to work. 

 Doing lspci reveals that the Macbook has a BroadCom BCM4328 802.11 a/b/g/n (rev03) chipset.  The chipset however does not appear in the Network tools, nor in other tools such as iwconfig, etc/network/interfaces file, and ifconfig.

I installed NDISwrapper, using the bcmwl5.inf/bcmwl5.sys drivers, and while they installed successfully, my wireless card is still not detected.  Any help will be greatly appreciated.

Thanks

---

### Post by cyberdork33 on 2007-11-08
> **addicted44 said:**
> I bought the latest Macbook (with X3100, base 2GHz model).  I have not been able to get the wireless on it to work. 

 Doing lspci reveals that the Macbook has a BroadCom BCM4328 802.11 a/b/g/n (rev03) chipset.  The chipset however does not appear in the Network tools, nor in other tools such as iwconfig, etc/network/interfaces file, and ifconfig.

I installed NDISwrapper, using the bcmwl5.inf/bcmwl5.sys drivers, and while they installed successfully, my wireless card is still not detected.  Any help will be greatly appreciated.

Thanks

What driver did you use? you have to use the driver for the 4328.

---

### Post by Zelut on 2007-11-09
> **cyberdork33 said:**
> What driver did you use? you have to use the driver for the 4328.

The newest macbooks use broadcom?  That sucks man.  Broadcom is one of the worst when it comes to wireless driver support and being open.

Have you tried installing the 'bcm43xx-fwcutter' package and running the bcm43xx-fwcutter.sh script that comes with it?  That is what I have to do on my older machine, but that is bcm4306 chipset..

---

### Post by cleentrax on 2007-11-09
I also have the new MacBook with the Broadcom 4328. I tried the bcm43xx-fwcutter, and had no success. But I didn't see any .sh script file. I used [this guide.]("http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom%20gentoo") No wireless networking option appears.

---

### Post by Threeethan on 2007-11-12
I am in the same book with you...I got stoked on the X3100/Santa Rosa Macbook and pulled the trigger, only to find that the broadcom card isn't autodetected.

I'm going to try the firmware from the mac dvds, though I'm running amd64 version of gutsy. 

Also, oddly enough, the broadcom product sheet for the 4328 claims that they have drivers for Linux...no downloads though.  Hard to say.

I'll report back here if I have any success (or even if I don't) but if anyone else can shed any light on the updated macbook's problems, that would be great.

---

### Post by cyberdork33 on 2007-11-12
> **Threeethan said:**
> I am in the same book with you...I got stoked on the X3100/Santa Rosa Macbook and pulled the trigger, only to find that the broadcom card isn't autodetected.

I'm going to try the firmware from the mac dvds, though I'm running amd64 version of gutsy. 

Also, oddly enough, the broadcom product sheet for the 4328 claims that they have drivers for Linux...no downloads though.  Hard to say.

I'll report back here if I have any success (or even if I don't) but if anyone else can shed any light on the updated macbook's problems, that would be great.

Use ndiswrapper and the Dell 4328 driver.
[I] [ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)
[/I] This one should work for 32bit or 64bit

---

### Post by cleentrax on 2007-11-13
> **cyberdork33 said:**
> Use ndiswrapper and the Dell 4328 driver.
[I] [ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)
[/I] This one should work for 32bit or 64bit

I've tried it on 64bit. No dice. It installs ok, but modprobe hangs, and the device never shows up for ifconfig, network applet, etc.

---

### Post by cyberdork33 on 2007-11-13
Yea sorry I don't know what to tell you unless you have some other error message or something. Is there anything in dmesg after you modprobe?

---

### Post by Threeethan on 2007-11-14
Hey thanks for that driver link -- it worked really well -- I used this tutorial: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

a simple unzip command was sufficient to get access to the files in that link, and then I used the rest of the stuff from that tutorial, and I'm golden.  Thanks a lot!

The [macbook page ]("https://help.ubuntu.com/community/MacBook")should probably be updated with info on the new broadcom drivers...plus some other issues I guess.  

Thanks again!

---

### Post by cleentrax on 2007-11-14
I tried that tutorial a couple of times. I am never able to get past the "sudo modprobe ndiswrapper" part. The terminal just hangs there.

To cyberdork33: I looked at dmesg. I don't understand most of what's going on in there, but I didn't see anything that obviously had to do with ndiswrapper, modprobe, etc.

Here's the last bit of results from dmesg for me:

```
[   50.702463] ppdev: user-space parallel port driver
[   50.853405] audit(1195095295.772:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5087 profile="/usr/sbin/cupsd"
[   51.188796] Failure registering capabilities with primary security module.
[   56.052713] [drm] Initialized drm 1.1.0 20060810
[   56.055607] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.056198] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   57.573325] NET: Registered protocol family 10
[   57.573480] lo: Disabled Privacy Extensions
[   67.739835] eth0: no IPv6 routers present

```

---

### Post by cyberdork33 on 2007-11-14
> **cleentrax said:**
> I tried that tutorial a couple of times. I am never able to get past the "sudo modprobe ndiswrapper" part. The terminal just hangs there.

To cyberdork33: I looked at dmesg. I don't understand most of what's going on in there, but I didn't see anything that obviously had to do with ndiswrapper, modprobe, etc.

Here's the last bit of results from dmesg for me:

```
[   50.702463] ppdev: user-space parallel port driver
[   50.853405] audit(1195095295.772:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5087 profile="/usr/sbin/cupsd"
[   51.188796] Failure registering capabilities with primary security module.
[   56.052713] [drm] Initialized drm 1.1.0 20060810
[   56.055607] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.056198] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   57.573325] NET: Registered protocol family 10
[   57.573480] lo: Disabled Privacy Extensions
[   67.739835] eth0: no IPv6 routers present

```
yea, I would guess the system is not even realizing that you are trying to load the module since it is not giving output.

I don't know why you are getting a hang. What version / flavor of Ubuntu are you using? The standard 64-bit? or is it like Ubuntu Studio or something?

---

### Post by cleentrax on 2007-11-14
> **cyberdork33 said:**
> yea, I would guess the system is not even realizing that you are trying to load the module since it is not giving output.

I don't know why you are getting a hang. What version / flavor of Ubuntu are you using? The standard 64-bit? or is it like Ubuntu Studio or something?

It's Ubuntu Studio. I guess I"ll try the regular desktop version and see if that makes a difference.

---

### Post by cleentrax on 2007-11-15
Got it working on 7.10 64-bit. So I guess there's a problem with ndiswrapper and Ubuntu Studio.

---

### Post by Levo75 on 2007-11-15
> **Threeethan said:**
> Hey thanks for that driver link -- it worked really well -- I used this tutorial: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

a simple unzip command was sufficient to get access to the files in that link, and then I used the rest of the stuff from that tutorial, and I'm golden.  Thanks a lot!

The [macbook page ]("https://help.ubuntu.com/community/MacBook")should probably be updated with info on the new broadcom drivers...plus some other issues I guess.  

Thanks again!

Do you use Gutsy or Feisty?

It didn't work for me in 32 bit gutsy. :(

---

### Post by cyberdork33 on 2007-11-15
> **Levo75 said:**
> Do you use Gutsy or Feisty?

It didn't work for me in 32 bit gutsy. :(

Should work the same way in either

Is ndiswrapper saying the driver is valid / loaded?

```
ndiswrapper -l
```

---

### Post by Tamiyadd on 2008-01-18
> **cyberdork33 said:**
> Should work the same way in either

Is ndiswrapper saying the driver is valid / loaded?

```
ndiswrapper -l
```

not working me to :(

```
 ndiswrapper -l
bcmwl5 : driver installed

```

why it isn't working :(

---

### Post by cyberdork33 on 2008-01-18
It should say that the hardware is found for that driver too. That driver does not seem to work.

```
cyberdork33@Grover-Ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
```

---

### Post by kop on 2008-02-07
I have the same problem.
Any news about it? 

I need the WiFi working :\


EDIT: 

woww.. it works (Macbook with Broadcam 4328 Wifi working - yes ):
Using: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-9192b3c227e128044894727c4b85a57abee8a0c9](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-9192b3c227e128044894727c4b85a57abee8a0c9)
Driver: [http://www.alex.conlinux.net/drivers/bcm4328.zip](http://www.alex.conlinux.net/drivers/bcm4328.zip)
> 
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant


Reboot and it works. :> Amazing. Thanks for all!

---

