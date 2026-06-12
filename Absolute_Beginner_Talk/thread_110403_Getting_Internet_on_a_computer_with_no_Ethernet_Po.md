---
title: "Getting Internet on a computer with no Ethernet Port"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by moneylosr20 on 2005-12-30
We're trying to get an old Toshiba laptop (with only a modem; no Ethernet port) to use the Internet via a USB to Ethernet Converter by SMC or a Wireless USB Network Adapter by Linksys. According to the Wired Ethernet troubleshooting [http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643") , it says the first step is to check whether or not the speed/duplexing is correctly negotiated. However, when we type in the command for the first step, we get an error from both the converter and adapter saying that "SIOCGMIIPHY on eth0 failed: Operation not supported". Should we download any drivers for the devices, or do some other commands?

Thanks,
-Bryan K.

---

### Post by jimrz on 2005-12-30
does it have a pcmia slot?

---

### Post by moneylosr20 on 2005-12-30
Thanks for the reply.

Yes, the laptop does have PCMIA slots.....but when we put in a wireless cardbus adapter, the laptop still doesn't connect to the internet :( . We'd prefer to use a USB to Ethernet converter rather than a wireless cardbus, but if there is no way a USB to Ethernet converter will work on Ubuntu, we can go with a wireless cardbus.

Thanks again,
Bryan K.

---

### Post by lleb on 2005-12-30
when you install the PCMCIA ethernet card (i am not clear what you are calling a usb - ethernet converter) what does dmsg spit out?  is Ubunbtu seeing the card when you install it in the system?

most ethernet cards be they onboard, PCMCIA or older PCI and ISA cards should be supported by all modern linux distros.

wifi on the other hand is a completely differnt beast and very nasty.  for that you can blame the manufactures for being so damn greedy.

---

### Post by moneylosr20 on 2005-12-30
Thanks for the reply.

Ubuntu does see the PCMCIA card, and allows us to configure the card, but even after we configure it, the card still doesn't work. (We can't show what dmesg spits out as we're a different computer to talk on the forums.) 

The "USB to Ethernet converter" we're using is a device manufactured by SMC that allows us to plug in an Ethernet adapter into a USB port (a webpage to a similar device can be found here: [http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&pid=279)]("http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&pid=279)")
)

Thanks.......again
-Bryan K.

---

### Post by jimrz on 2005-12-30
does your old toshi even support wifi? you can pickup a pcmia 10/100 ethernet card pretty cheap anymore. i still carry my old D-link DFE-650 in my laptop bag for use when wifi not available but wired ethernetis, since my old thinkpad does not have onboard nic. this still works all the time without fail.

---

### Post by coredump on 2005-12-31
Have you tried the second step of that debugging list?  The one that goes 'ifconfig eth0'?  That's much more universal and shouldn't fail in the way that the first command did.

If you try 'ifconfig', and eth0 does not work, try 'ifconfig -a' to see all network interfaces (with the USB gadget plugged in, of course).  If you can't get the USB gadget to show up as either 'eth0' or some other device name, then you'll need to diagnose USB trouble.  This might be due to the lack of a USB driver, or lack of a suitable driver for the gadget itself.

Once you've got 'ifconfig' working, you should be able to set up an IP address and start testing the interface with 'ping'.

---

### Post by Calindae on 2008-03-23
I found this thread via google and i figured i wouldn't waste another thread elsewhere, and I have a similar question. I got this old desktop from someone and it doesn't have an ethernet port or usb ports. Am I going to be able to get internet on this dino? I haven't even turned it on yet because it smells so bad of cigarette smoke, I don't want to blast my house with it, so i don't even know if the beast runs or not...
I'm not really a pc expert, so does anyone know of common ports on old units that would be used instead of usb? I've only worked with newer laptops that have no problem with hardware connectivity (i.e. three usb ports).

---

