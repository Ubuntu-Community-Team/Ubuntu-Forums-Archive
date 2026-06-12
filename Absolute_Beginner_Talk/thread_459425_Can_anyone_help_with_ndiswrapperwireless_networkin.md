---
title: "Can anyone help with ndiswrapper/wireless networking"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by neilw on 2007-05-30
Hello,
I'm new to ubuntu and have tried all night, including following threads here, to get my wireless usb adapter working (my ethernet works fine, I've just moved my router so need it wireless). I have a BT Voyager 1055, which I believe is some kind of broadcom.

Anyway, I've done the following:

1. installed ndis library
2. added my bcmrndis.inf and installed it using ndiswrapper and is listed ok in the gui (and ndiswrapper -l says 'bcmrndis driver present, hardware present)
3. copied the driver .sys files (I put in rndismp.sys, usb8023.sys, bcm43xx.cat, rndismpk.sys, usb8023k.sys) in the etc/ndiswrapper/bcmrndis directory
4. I copied the 99-custom.rules file to the udev/rules.d directory and the idproduct/idvendor entries match what I found in the hardware list (not that I know what it is or how it's used) using lshw (the entry is there under usb:1 with the configuration saying driver=ndiswrapper)
5. I've ran sudo modprobe ndiswrapper and sudo ndiswrapper -m, and on re-running modprobe -m, it tells me the modprobe config already contains alias directive, so I guess that must be set ok
6. /etc/modprobe.d says 'alias wlan0 ndiswrapper'
7. I've rebooted. The only entry in my system log for ndis says stuff like:
registered new drive rndis_host
ndiswrapper version 1.8 loaded
loadndiswrapper failed (65280)
ndiswrapper: probe of 3-4:1.0 failed with error -22
registered new driver ndiswrapper

When I look in system/admin/networking gui it only lists ethernet and modem, ifconfig lists eth0 and lo only, iwconfig finds nothing.

Can anyone help? I'm stuck now and finding it difficult to understand why (after searching forums and trying to find anything useful in the ubuntu website) linux/ubuntu is so bad with regard setting up wireless equipment and every site is so different with regard to setting up wireless equipment.

thanks.

Neil.

---

### Post by Ek0nomik on 2007-05-30
Well, the first step to trying to help you woudl be figuring out what kind of card you have.

What does the command:

```
lspci
```

output?

---

### Post by scrooge_74 on 2007-05-30
Sorry you are having so much trouble, I have only had to setup a couple of  cards using ndiswrapper and the howtos for those cards were very straight forward.  I usually try to get hardware which has native linux support.

---

### Post by bigspottycat on 2007-05-30
Don't know if this would work with your card but here's the link to a reply i posted a while back for someone who was having difficulty getting their broadcom wireless card to work:

[http://ubuntuforums.org/showthread.php?t=274001](http://ubuntuforums.org/showthread.php?t=274001)

Hope this helps.

---

### Post by tyres on 2007-05-31
Hi,

Can you post the output of some commands, so we can see what the system is reporting?

Post the ouput of 'ifconfig','iwconfig','lsusb', and the contents of your 
'/etc/udev/rules.d/99-custom-rules' script. That should give us something to go on.

What version of ndiswrapper are you using?

Do you have a config file called something like '1690:0715.F.conf' in your /etc/ndiswrapper/bcmrndis directory?

Just re-reading your post, I think you may have the wrong values for idproduct/idvendor, as the usb:1 line you pointed to in the output of 'lshw' is not what you should be using, at least in the output of 'lshw' when I run it on my system.

You should run 'lsusb', and there should be a line (among others) like this;

'Bus 002 Device 003: ID 1690:0715 Askey Computer Corp. [hex]'

The values there (1690:0715') should match the values you put in your '/etc/udev/rules.d/99-custom.rules' script.

If the BT1055 is being recognised, the ouput of 'ifconfig' should show you a 'wlan0' device, which is your wireless adapter.

---

