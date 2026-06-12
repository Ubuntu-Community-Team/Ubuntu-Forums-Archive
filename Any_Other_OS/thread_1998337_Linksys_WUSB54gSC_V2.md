---
title: "Linksys WUSB54gSC V2"
date: 2012-06-06
forum: Any Other OS
---

### Post by neuman1812 on 2012-06-06
Running Mint 12(Lisa) 32 Bit
Laptop Satellite a85
Wireless USB adaptor - Linksys m:WUSB54gSC ver.2

SO Im attemptign to use the USB device because the onboard Wireless and Network are borked.   I get an error message about PCI conflict at startup.   Searching the web determined the Wirless and Lan are fubar.

So Im trying this USB device.

NDISGTK that is build in see the driver and Device "Hardware present"

ndiswrapper -l
```

ndiswdm : Driver installed
                 Device (1737:0075) Present

```

lsusb :
```
 
Bus 001 Device 004: ID 1737:0075 Linksys WUSB54GSC V2 802.11g Adaptor

```


However under lshw  It does not list network at all.  I unfortunally cannot get the full output to post because I have no way to transfer a file from that computer.   But I have checked it several times in verbose mode and there is no "-network" section listed.

any suggestions?

---

### Post by Perfect Storm on 2012-06-06
Moved to Other OS/Distro Talk.

---

### Post by O2Blevel on 2012-06-06
Are you sure your wireless card doesn't use the rt73 driver. At one time I had a WUSB54gc card which used the rt73, no need for ndiswrapper.

---

### Post by neuman1812 on 2012-06-06
i have no idea if its uses that driver or not.. 

 Before I even tried the wrapper options..I just plugged it in.   Nothing happened. the network manager doesnt show it listed as a vaild option to configure.

---

