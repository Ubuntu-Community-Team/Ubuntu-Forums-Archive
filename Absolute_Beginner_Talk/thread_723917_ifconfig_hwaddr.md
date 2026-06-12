---
title: "ifconfig hwaddr"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2008-03-14
does the 'hwaddr' output from ifconfig refer to your NIC's actual MAC address?

---

### Post by wormser on 2008-03-14
Yes.

---

### Post by alphaniner on 2008-03-14
So if it changes after a reboot, that is a bad thing, yes?

eth3            link encap:Ethernet Hwaddr 00:00:6C:13:F1:31

<reboot>

eth4      Link encap:Ethernet  HWaddr 00:00:6C:7F:B2:CB

---

### Post by wormser on 2008-03-14
> **alphaniner said:**
> So if it changes after a reboot, that is a bad thing, yes?

eth3            link encap:Ethernet Hwaddr 00:00:6C:13:F1:31

<reboot>

eth4      Link encap:Ethernet  HWaddr 00:00:6C:7F:B2:CB

eth3 and eth4 are different network adapters.  Maybe your system is creating a new adapter because of some issue.  Have you installed any new programs?  What is your set up?

---

### Post by alphaniner on 2008-03-14
It is not mine, it is from someone I was trying to help.  I mentioned this thread to him and asked him to post the output of a few more *ifconfig*s, but I already wasted a bunch of his time with my 'help' so I'm not sure he'll bite.  The thread is [here]("http://ubuntuforums.org/showthread.php?t=723813&page=2").  Each time he restarts his computer his eth<number> increases by one and in the two ifconfig outputs he posted the HWaddr is different.  He was up to eth5 at last count.  The card works with windows, though.

DarkMartyr:  If you are up for it, run the 'ipconfig /all' command in windows, copy down the "Physical Address" line, then restart and do it again.

---

### Post by alphaniner on 2008-03-14
ifconfig -a only showed eth3, then after reboot eth4, then after reboot eth5.  Each time there is only one eth#.  Besides, I'm pretty sure he doesn't have that many adapters.

---

### Post by DarkMartyr on 2008-03-14
I'm the guy he was trying to help.

Here is the first output I posted. I'd like to note when I first installed my computer did start at eth0.

eth3            link encap:Ethernet Hwaddr 00:00:6C:13:F1:31
                   inet6 addr: fe80: :200:6cff:fe13:f131/64   Scope:Link
                   UP BROADCAST RUNNING MULTICAST   MTU:1500 Metric:1
                   RX packets:6430 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0  txqueuelen:1000
                   RX bytes:388068  (378.9 KB)    TX bytes:6075  (5.8 KB)
                   Interrupt:17  Base address:0x8000


then after a reboot ifconfig was:

eth4      Link encap:Ethernet  HWaddr 00:00:6C:7F:B2:CB  
          inet6 addr: fe80::200:6cff:fe7f:b2cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26940 (26.3 KB)  TX bytes:5124 (5.0 KB)
          Interrupt:18 Base address:0x4000 


I am up to eth5, but I'm on my other partition atm (vista).
more background information follows.

Compaq Presario f755
lspci says Nvidia for my network adapter, but doesn't recognize the device (don't have the exact output)
I have installed ubuntu on my desktop, but this is my first laptop install. Semi-newb to linux, but I know some basics so just tell me what you need and I will hurry back with the results.

---

### Post by wormser on 2008-03-14
> **alphaniner said:**
> ifconfig -a only showed eth3, then after reboot eth4, then after reboot eth5.  Each time there is only one eth#.  Besides, I'm pretty sure he doesn't have that many adapters.

That is what I was thinking it was doing.  I have no idea what would cause this.  The only thing I can suggest is check what software has been installed lately.  Sorry, I cannot do more.

---

### Post by DarkMartyr on 2008-03-14
00-1B-24-E9-80-FF

Physical address from windows ^ pre-restart
Post-restart the address is the same.

no applications have been installed this is a fresh install all that has been enabled in the restricted driver for my wifi card (doesnt work) I'll try disabling that and trying my eth again

---

### Post by wormser on 2008-03-14
Try find the exact model number of the card.  Post the results and start searching the forums for it.

---

### Post by alphaniner on 2008-03-14
I tried searching the forums and the web for info on your laptop and ubuntu, and only your post came up lol.  So unfortunately we don't have any giants' shoulders to climb upon.  

You said ubuntu doesn't recognize the device, if you could post the exact output that might be helpful.  Not to me - I'm in waaaay over me head - but maybe to somebody.  Also if you could get some detailed specs from the manufacturer that might help too.  It must be a driver issue, but whether or not it's slouble is anybody's guess.  I gotta get my beauty sleep now.  Good luck.

---

### Post by DarkMartyr on 2008-03-14
I did some searching and the only info I've been able to pull up about my ethernet is that it's using Nvidia nForce network controller. (same as my desktop which works with ubuntu) I dont know what my chipset is. How can I find that out?

---

### Post by DarkMartyr on 2008-03-14
lspci output:

```
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

is it just me or does that not even list my NIC? All I see is my wireless card listed.

---

### Post by wormser on 2008-03-14
> Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)

That is the card but it says Unknown device.  I started googling it in quotes and found somebody else with the same issue.  We just need to keep searching the net until we find the solution.

I found [this]("http://ubuntuforums.org/showthread.php?t=700590") but I am not sure if it will work.

---

### Post by DarkMartyr on 2008-03-14
Seems he has the same problem as me, but the thread just ends :\ I went into the network tools, but my hardware adress just says not abailable. Should I just input the mac address I got from windows?

---

### Post by wormser on 2008-03-14
> **DarkMartyr said:**
> Seems he has the same problem as me, but the thread just ends :\ I went into the network tools, but my hardware adress just says not abailable. Should I just input the mac address I got from windows?

That is why it is always good to post your solution at the end and mark it as resolved.  

Yeah, just use your xp mac number.  I am thinking this probably is a bug or just poor support for your hardware.  But, give it a shot and post the results of that file suggested.  If it does not work then keep on searching the web.

---

### Post by DarkMartyr on 2008-03-14
I got it to work, but after I restarted I had to reconfigure the interfaces file and now it doesn't work o.0 all I changed from eth7 to eth8.

I configured it to use dhcp and it failed twice and the third address was excepted and I could get on. Now it's doing the same thing as before!

>.< come on Gutsy work with me here

I didn't put the hwaddress ether blah blah in the right place because it said it couldnt read interfaces when i tried to restart the network.

I have it configured this way

Auto lo
iface lo inet loopback

auto eth8
hwaddress ether mac here
iface eth8 inet dhcp

---

### Post by DarkMartyr on 2008-03-14
Changed it so iface eth8 inet dhcp comes first then the mac address
restarted network and got the same output as before although it does have the right mac now

Here is the trouble. I have it working now, but I still have to reconfigure the file everytime with the new eth#. Upon reboot it changed the mac address. I gather this is because Ubuntu is looking for eth9 and interfaces is giving eth8 the right mac address. eth8 no longer exists. So we have to figure out why ethX keeps going up and changing mac addresses. At least we made some progress

---

