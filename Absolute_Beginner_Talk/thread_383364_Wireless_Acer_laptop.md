---
title: "Wireless Acer laptop"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-03-13
Im trying to install wireless on a Acer aspire 3500..  can anyone point me to a howto where I can do this?

The output of lspci is:

> user@user-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
user@user-laptop:~$ 



Any idea's?

---

### Post by Zzl1xndd on 2007-03-13
not sure if it will be help full but my toshiba m70 also uses an Atheros the only thing I did was install Network manager and it worked.

---

### Post by sstakes1 on 2007-03-13
I do not have this laptop or experience with atheros cards. Your laptop has an atheros wireless card and people have mixed experience with it. To see if Ubuntu has recognized the card, type in the following command

```
sudo iwconfig
```

See if your card shows up, usually as ath0. If no adapters with wireless interface is indicated, then  you have to do a little more work. Try searching the forum for atheros wireless and see if any of them have the solution for you. 

If you do find wireless extensions, you may use Wifi-Radar or NetworkManager to ease your connections to the wireless access points. Again Search the forums or the HowTos for using these wonderful programs.

HTH

---

### Post by aktiwers on 2007-03-13
Typing that command gives this output: 
> user@user-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

user@user-laptop:~$ 


---

### Post by sstakes1 on 2007-03-13
Okay. That means you have to do more work in getting the drivers installed correctly. Try searching the forums for acer and wireless and see if there is something that can help you.
I found this [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224350&highlight=acer+%2Bwireless")  that may be of some help.
Otherwise try posting this in the laptop forum. 
Sorry, I do not have this laptop nor experience with this wireless card.:( 
Good Luck

---

