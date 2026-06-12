---
title: "Network setup"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by dblbogey on 2006-02-28
Ok, I'm a newbie, but I do understand basic hardware, and I'm fairly adept with Windows, so I'm ready to give Ubuntu a try. I've installed 5.04 on my PII twice, but Ubuntu isn't seeing the network connection. After the first install, the Network Services window showed the computer's modem, but not the NIC (it worked fine under Windows, so I know it's not a card problem). The second install didn't see either one. In neither case did the window offer an 'add' button to add an additional interface device.

Also, I've read some in this forum and the Unofficial Starter Guide, and I don't understand the references to 'sudo'. Please explain how to execute sudo commands.

Thanks in advance.

---

### Post by ConkreteDisko on 2006-02-28
To enter the "sudo" commands go to...App menu -> Accesories -> Terminal

You type them in there (think DOS..all command based)

---

### Post by shof2k on 2006-02-28
sudo enables you to execute a terminal command with full adminstrator (or root in linux speak) privellages.  

It's format is:
```
 sudo (command to run) 
```

With your networking issues, open a terminal and type

ifconfig

Paste the results and let people try and help you find out what's wrong.
Also did the Ubuntu install detect your network or did you add the card afterwards?

---

### Post by dblbogey on 2006-03-01
[QUOTE=shof2k]sudo enables you to execute a terminal command with full adminstrator (or root in linux speak) privellages.  

It's format is:
```
 sudo (command to run) 
```

With your networking issues, open a terminal and type

ifconfig

Paste the results and let people try and help you find out what's wrong.
Also did the Ubuntu install detect your network or did you add the card afterwards?[/QUOTE]

**********
Thanks for the info, the card was in the machine and connected to my DSL modem, when I installed Ubuntu. The green light is on. When I typed ifconfig, this was the response:

          Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5755022 (5.4 MiB)  TX bytes:5755022 (5.4 MiB)

Network Settings doesn't show the NIC, and there isn't an 'Add' button to tryt to add mine into the system.

---

### Post by jamesr on 2006-03-01
what is the type of NIC, brand name? 

post the outpot
dmesg |grep eth0

---

### Post by darth_vector on 2006-03-01
can you post the output of```
lspci
```it sounds like your network card hasn't been detected by the system. the above command prints out all PCI devices that the system knows about.

---

### Post by dblbogey on 2006-03-02
It's been so long that I cannot remember the make, much less the model. I'm sure it's a very common NIC by Dlink, 3Com, Linksys or one of the like.

As for the code, "lscpi", I received a "command not found" response.

---

### Post by dblbogey on 2006-03-02
Opps! reading my own reply just now, I realized that typoed the command. resubmitting correctly I got a list, as follows:

0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:09.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)
0000:00:11.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
0000:00:12.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:12.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:12.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
doug@luigi:~$

I don't see a NIC in the list, but maybe I don't know what to look for.

---

### Post by jamesr on 2006-03-02
yes it seems that it not being seen, all the more reason to id the card. It is possibly an ISA card

---

### Post by sony102600 on 2006-03-03
hey guys, I seem to be having a similar problem, cannot connect to the interenet, I am on a university network, not through wireless, and it says my eth0 is active.... here are some important outputs

dhclinet

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on LPF/sit0/
Listening on LPF/eth0/00:13:8f:73:e8:e9
Sending on LPF/eth0/00:13:8f:73:e8:e9
Listening on LPF/lo/
Sending on LPF/lo/
Sending on Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo ifconfig -a

eth0 Link encap:Ethernet HWaddr 00:13:8F:73:E8:E9
inet6 addr: fe80::213:8fff:fe73:e8e9/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:3194 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:7 dropped:0 overruns:0 carrier:7
collisions:0 txqueuelen:1000
RX bytes:1163970 (1.1 MiB) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0xe400

lo Link encap:Local Loopback
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:102840 (100.4 KiB) TX bytes:102840 (100.4 KiB)

sit0 Link encap:IPv6-in-IPv4
inet6 addr: ::127.0.0.1/96 Scope:Unknown
UP RUNNING NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:11 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by shof2k on 2006-03-03
Your issue is slightly different in that your PC can 'see' your card but you're not getting an ip address from your universities DHCP sever.

Confirm you're allowed to connect to your Uni network and have a chat with their network admin peeps.

hope that helps

---

### Post by dblbogey on 2006-03-03
[QUOTE=jamesr]yes it seems that it not being seen, all the more reason to id the card. It is possibly an ISA card[/QUOTE]

It is a 3Com, Etherlink III from 1997; Assy: 03-0020-0101, Rev A. Looks like it's fairly ancient and is only 10 Mbps. It worked fine under Windows. What is an ISA card?

---

### Post by Iowan on 2006-03-03
The 3Com Etherlink III - AKA 3C509B - is an ISA card.  On some of my other systems, it behaves like a PCI card (auto-detects the address and IRQ).  I've unsuccessfully tried to install Ubuntu on a couple of machines with these cards.  May need different drivers.
  An ISA card has a card-edge connector that's about 5.5" long with a notch in the middle.  Contacts are approx. 1/16"  wide.  An EISA card has the same card-edge dimensions, but the contacts are only about half as wide (the notch is slightly deeper - ISA cards will fit into an EISA socket, but not vice-versa).  The "other" style card you'll *normally* see is the PCI card which has  a shorter card-edge connector and narrower contacts.

---

### Post by jamesr on 2006-03-03
An ISA card defines the slot and the bus that the card connects to.
The 3Com, Etherlink III from 1997, is an ISA slot card.
Another point is that ISA connectors on the the MOBO are black in colour and the standard is PCI card where the connector on the MOBO is white in colour. If you are interested I can take pictures on the connectors on a MOBO and the cards themselves and post them.

But back to the case in hand, Ubuntu does not recognise the 3com509B automatically but it easy to add manually and if this works we can edit the appropiate files
Do not reboot during this process.

At the console prompt

```
sudo modprobe 3c509
```

nothing seems to happen but if you now do 

```
sudo ifconfig -a
```

the output should show eth0

then
```
sudo dhclient

sudo ifconfig -a
```

output should show an address

and it should work.

If all is ok, I can supply rthe changes needed so this happens every time you boot.

---

### Post by dblbogey on 2006-03-04
Yahoo!!  Bravo, jamesr, it worked. Now, I would be most pleased to have directions on how to recognize the NIC on boot-up.

BTW, thank you and Iowan for the lesson on card types. PCI has been around long enough that I had forgotten all that stuff (like DOS!)

Regards to all who helped,   Doug

---

### Post by jamesr on 2006-03-04
```
sudo nano /etc/modules
```

add a line at the end 3c509

close file and save

```
cat /etc/network/interfaces
```

Post output

The usual is that you need to add two lines at the end but first post the file.


auto eth0
iface eth0 inet dhcp

---

### Post by dblbogey on 2006-03-05
The loopback network interface reads as follows:

auto lo
iface lo net loopback

---

### Post by jamesr on 2006-03-05
You should only need to do```
sudo dhclient
```to get it working. 
```
sudo ifconfig -a 
```should show eth0

final stage ```
sudo cp /etc/network/interfaces /etc/network/interfaces_bck
sudo nano /etc/network/interfaces 

```
add the lines

auto eth0
iface eth0 inet dhcp
at the end of the file.Should look like
# comments athe beginning

auto lo
iface lo net loopback


auto eth0
iface eth0 inet dhcp

Save and should work upon reboot.

---

### Post by dblbogey on 2006-03-05
It worked fine until I rebooted. Now it's gone. I suspect that I didn't properly save the files that I altered. How is the proper way to save such? I guess I'll start again with your instructions and see if I can rebuild the changes/

---

### Post by jamesr on 2006-03-07
With Nano I think the sequence is.

cntrl x    ;to exit
yes        ;save file
return     ;accept name

---

