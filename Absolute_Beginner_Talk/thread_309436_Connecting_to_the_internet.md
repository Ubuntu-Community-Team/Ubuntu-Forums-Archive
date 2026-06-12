---
title: "Connecting to the internet"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by KentS on 2006-11-29
I have just installed Ubuntu Dapper Drake for x86-machines. This is my first experience with Linux, so i basically don't know where to begin or what to do. My current problem is connecting to the internet (ADSL) via cable.

I'm running Ubuntu on a HP Pavilion dv2004ea. My PC is connected to an external Belkin firewall/router by cable. The Belkin firewall is connected to a Cellpipe(?) modem/router provided by my ADSL provider.

I tried my internet connection using the Live CD, and it worked perfectly. I think the PC also downloaded something during the installation process, since it has received several packages. 

According to my Network tool, I have two network units:
Ethernet interface (eth0) which have received 5 packages and Loopback interface (Io) which have received 7 packages.

I tried to type "sudo pppoeconf" in the terminal. The output in the program was
"Sorry, I svanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the svan failure may also be another running pppoe process which controls the modem."

The output on the terminal was
"SIOCSIFFLAGS: No such file or directory
sendPacket: send: Network is down
SIOCSIFFLAGS: No such file or directory
sendPacket: send: Network is down"

When I try to ping my router I get
"connect: Network is unreachable"

I would appreciate any suggestions for what I can do, but please go easy on me.

---

### Post by smile_sunshine on 2006-11-29
um possibly use dhclient  - ("dhclient  eth0" from command line) - not sure but might be worth trying?

---

### Post by bradleyd on 2006-11-29
on the live-cd did you have to use pppoe to connect to internet, or was it all configured for you?I believe the Belkin should handle the pppoe authentication.

---

### Post by 56phil on 2006-11-29
Can you ping your router?[HTML]ping -c5 192.168.1.1[/HTML] just replace 192.168.1.1 with the IP address of you router.

---

### Post by KentS on 2006-11-30
I'm now writing this on Ubuntu. Running dhclient seems to have done the trick. But there is one problem. I have to run dhclient every time I restart Ubuntu. It doesn't seem to receive any IP adress automatically.

Before I receive an IP adress, my PC doesn't detect any network. Trying to ping my router just gives me a message about no available network. 

I tried to hook up my computer on several places on the network. Once I got an IP adress beginning with 193. I've never received such an IP adress before. In any case, I was not able to use this adress to communicate with any network. When pinging I was able to send packages, but didn't receive anything.

I didn't have this problem when running the Live CD. Then, everything was configured for me, and I received an IP adress automatically.

Do you have any ideas how I can receive an IP adress automatically?

---

### Post by simon303 on 2006-11-30
Ive just installed Ubuntu on my computer and it won't connect to the internet.
Infact it can't even detect my ethernet card and im unable to follow the manufacturers instructions for installing the drivers as Ubuntu obviously differs in setup from the type of system they expect to be used.
Im using a Belkin desktop Network PCI Card
I would be gratefull for any hints/tips/solutions that my get it working

---

### Post by louieb on 2006-11-30
KentS,
Try going System>Admin>Networking.
Click on eth0 and select properties.
Check to see if Configuration is set to DHCP.
That should set you up.

---

### Post by simon303 on 2006-11-30
i would if i could, but as far as my computer is concerned eth0 doesn't exist
i need to tell it that it is there by installing drivers but can't do that either

---

### Post by bradleyd on 2006-11-30
simon post your results from lspci and dmesg.

---

### Post by simon303 on 2006-11-30
result of lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller:  Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
01:05.0 VGA compatible controller: nVidia Corperation NV11 [GeForce2 MX/MX 400] (rev al)
```

sorry, i can't post dmesg results as i have to copy them by hand to another machine

---

### Post by simon303 on 2006-11-30
i have been informed that Ubuntu alraedy has the needed drivers, it just can't "see" the ethernet card
does anyone know of a way of making it "see" the card?

---

### Post by KentS on 2006-11-30
louieb,
The configuration for eth0 was already set to DHCP. So that didn't solve the problem. But thanks for the suggestion.

---

### Post by bradleyd on 2006-12-04
simon this belkin nic card is a pci card(internal)?

---

### Post by simon303 on 2006-12-05
yes
it is a internal pci card
based on the realtek rtl8139 chipset if thats any use

---

