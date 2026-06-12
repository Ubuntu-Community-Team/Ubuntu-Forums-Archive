---
title: "Macmini 2011 USB boot problem"
date: 2024-05-29
forum: Apple Hardware Users
---

### Post by northernmonkey2 on 2024-05-29
Hi all, I&#8217;ve had a a great experience with Ubuntu bringing an old Mac Mini 2011 back to life! I do now need to adjust partitions and wanted to boot from a Gparted boot disk. However, I can&#8217;t now seem to select the USB stick when booting. I&#8217;ve tried every possible USB port, as well as two (pc) wired and wireless keyboards, ensuring the &#8220;Alt&#8221; key is held after power on.  When I installed Ubuntu could I have replaced the original Mac Boot Selector?+

FYI my efibootmgr says this if that&#8217;s any help;

```

BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000,0080
Boot0000* ubuntu
Boot0080* 
BootFFFF*

```

---

### Post by gezzer2 on 2024-05-29
not sure if this is of any help but you may need 
ReFind to make the USB bootable

[https://www.howtogeek.com/213396/how-to-boot-a-linux-live-usb-drive-on-your-mac/](https://www.howtogeek.com/213396/how-to-boot-a-linux-live-usb-drive-on-your-mac/)

Refind should be available from the software store or synaptic. thats as far as my knowledge goes with a mac ..

---

### Post by northernmonkey2 on 2024-05-31
Thanks for the tip - I had read about that tool but still can’t understand why I don’t even get the Network Boot option. I’ll try disconnecting the hard disk and try booting that way first before your suggestion. Cheers

---

### Post by QIII on 2024-05-31
Moved to **Apple Hardware Users**

---

