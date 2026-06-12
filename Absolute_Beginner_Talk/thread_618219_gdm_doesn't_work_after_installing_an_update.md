---
title: "gdm doesn't work after installing an update"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by walix on 2007-11-20
Hi all,

Yesterday I installed a bunch of updates and among them there was an update for gdm. I have realized this morning that gdm doesn't work anymore. It gets stuck on boot (I get a gray screen with a cross in the middle).

The message I get when visualizing the /var/log/daemon.log is this:

 Nov 20 12:26:56 infopc163 gdm[5571]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Nov 20 12:26:56 infopc163 gdm[4877]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 

I tried to look into the gdm.conf file and everything seem to be ok. However, I'm not very confident which such linux configuration files. Any help would be appreciated.

Thanks and best regards

---

### Post by conjur3r on 2007-11-20
What does your /var/log/Xorg.0.log say?  You can do a search for EE to locate all the errors.

What video card do you have and what drivers do you use?

---

### Post by walix on 2007-11-20
> **conjur3r said:**
> What does your /var/log/Xorg.0.log say?  You can do a search for EE to locate all the errors.

What video card do you have and what drivers do you use?

Here the info from /var/log/Xorg.0.log

(EE) RADEON(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.


And here the info about the video card from the xorg.conf file

Section "Device"
        Identifier      "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection


Thanks for your prompt reply.

---

### Post by taurus on 2007-11-20
Reconfigure your X again but try using **vesa** driver until you get X up and running again. Then, install an ATI driver for your graphic card.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by walix on 2007-11-21
> **taurus said:**
> Reconfigure your X again but try using **vesa** driver until you get X up and running again. Then, install an ATI driver for your graphic card.

```
sudo dpkg-reconfigure xserver-xorg
```

It works after reconfiguring X, thanks for your help. 
However, I didn't find in the options this vesa driver you mention and I used ati when it asked for the driver choice. Is this a problem for X to work well?

Regards.

---

