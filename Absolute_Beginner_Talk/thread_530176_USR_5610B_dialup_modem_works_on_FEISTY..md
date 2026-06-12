---
title: "USR 5610B dialup modem works on FEISTY."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by funsport on 2007-08-20
I am very new to linux and was very pleased with Ubuntu 7.04 (actually Kubuntu because ease of use of KPPP). I  was much happier when I got my USR 5610B internal pci dialup modem working in Feisty Fawn, FINALLY!! 

I have digested all the information on the web and combined all into the following to make my dialup work. This process could apply to other full hardware modems too (not winmodems!!)

In the Terminal:
   1.  Type:     wvdialconf
        Response:   should respond with which ttyS? that the modem was actually found. This will answer which ttyS the modem resides instead of guessing where it is. Mine was found in ttyS1. You must forget what WINDOWS is reporting because the USR 5610 documentaion says it will always use COM5 and from all the sites I have seen, everyone was saying it has to be ttyS4.


  2.  Type:      lspci -v
       Response:    Look for the description for your modem. It will be under the serial controller section.  You will need :

          I/O ports at ####    (mine was d000,  when you enter this port info in setserial, it will be in hex notation i.e.   0xd000
          IRQ                      (mine was 11)

You now have the 3 information you need pointing at your modem without any guesswork.  My modem uses : ttyS1  , port 0xd000,  irq 11

  3. You must now download the setserial command. This means you will have to access the internet somewhere else to do the download.
Feisty Fawn does not have it on first install. To verify :
            Type:   which setserial             ('which' is a linux command)
            Response:   you should get a directory path to the setserial command if you have it already installed or else you'll get a file not found or simply no response.

     Install the setserial.deb you just downloaded:
              Type:    sudo dpkg -i setserial.deb

    Verify that setserial was installed by typing 'which setserial'.
       my Reponse was : /bin/setserial

   4. Now you will set your modem with the setserial command:  
             (I will use my settings for the example. Use your settings of ttyS# , port 0x#### , and irq #)

          Type:     sudo setserial /dev/ttyS1 uart 16550A port 0xd000 irq 11 baud_base 115200 spd_vhi skip_test

  5.   My computer now knows the USR5610 as ttyS1  with port 0xd000  and irq 11,
        You must link this ttyS1 to the modem for the dialup software.

        Type:  sudo ln -sf /dev/ttyS1 /dev/modem

  6.   The dialup tool I like is KPPP (the internet dialup tool in Kubuntu, with KDE). You should be able to dial out.  I am using PeoplePC so the user Id to use is [email]username@peoplepc.com[/email]


The only problem I have now is everytime I reboot the computer, the link to the modem is lost. Is there anyone who can tell me where to put that link statement so that it will execute when computer reboots? Thanks.

---

### Post by Bartender on 2007-08-20
Hi, funsport -
That's some impressive work you did.
I've been telling people that PeoplePC won't work with Linux because of the proprietary software they use.  But you say you're using it?  Did you have any problems getting the modem to make a connection with their servers?
I'll have to stop saying that about PPC if it's not true!

Sorry, i don't know how to make the modem link permanent.

---

### Post by funsport on 2007-08-20
Hi Bartender,
    My ISP is PeoplePC (PPC). 
    Someone on the net had posted in detail how to configure the KPPP and that was where I got the idea to use :
           [email]username@peoplepc.com[/email]
   
     No problem in connecting with  PPC servers. Make sure the configuration of the dialup software  is correct i.e. Baud rate= 115200,  CHAP 

   I will have to try out other distros to see if by using wdialconf and lspci to get the required ttyS#, port #### and irq # to see if it will make my modem work. Maybe other distros will keep the the link permanent.

---

### Post by funsport on 2007-08-21
I may have prematurley stated that ONLY hardware modems would work with my instructions above.

I don't have a softmodem to verify but why couldn't a softmodem with the proper driver installed work with my instructions above? I would think that once the driver was installed, **wvdialconf** would find that modem and report which ttyS# the modem is on.The rest of the instructions would be the same.  

I would be curious if anyone has one of these softmodems and followed the instructions above to see if the modem will finally work to get on the internet.

---

### Post by funsport on 2007-08-21
The process of writing and executing a custom script for boot time seems to be a standard process. 

This link is an excellent tutorial for script writing shown on youtube and this solved my problem of writing my modem/ttyS1 connection on boot:

youtube.com/watch?v=d39izaupvEg

---

### Post by funsport on 2007-08-24
The process would be more complete if I had given a link to download the setserial command for debian OS platforms in Step 3 above:

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=setserial](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=setserial)

---

### Post by _duncan_ on 2007-08-24
I don't have my feisty live cd so I couldn't check, but I think the setserial package is included in the CD. It's not installed by default, but can be installed using synaptic package manager from the CD without downloading anything.

---

### Post by IusedTObeSOMEONEelse on 2007-08-24
Looking to see how it works out for me as I may be having to use dial up soon due to no DSL or high speed where I am moving to, this is what terminal spits out:

** wvdialconf**
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
**and this::**

 lspci -v
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: IBM Unknown device 01e1
        Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 01e1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: feb00000-febfffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05) (prog-if 80 [Master])
        Subsystem: IBM Unknown device 0205
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fff0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0205
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at fb00 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
        Subsystem: IBM Unknown device 0205
        Flags: medium devsel, IRQ 9
        I/O ports at fe00 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0205
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at fb80 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: IBM Unknown device 0205
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at f000 [size=256]
        I/O ports at f400 [size=64]

01:00.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem (prog-if 00 [Generic])
        Subsystem: ARCHTEK TELECOM Corp Unknown device 9100
        Flags: medium devsel, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 7800 [size=256]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
        Subsystem: IBM EtherExpress PRO/100 VE
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 74c0 [size=64]
        Capabilities: <access denied>
[B]
Ok, so there is a modem in machine but not picked up. any ideas would be most helpful.[/B]

---

### Post by Bartender on 2007-08-25
> **MustangSallydd said:**
> 
01:00.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem (prog-if 00 [Generic])
        Subsystem: ARCHTEK TELECOM Corp Unknown device 9100
        Flags: medium devsel, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 7800 [size=256]
        Capabilities: <access denied>

There it is, in your list of identified devices.  I've zero experience getting winmodems to work, but have seen this modem mentioned many times on Ubuntu Forums.
Good luck

---

### Post by funsport on 2007-08-28
Hi Mustang,
    Barttender highlighted your modem.
    I did a search on your modem, and found this link.

linmodems.technion.ac.il/packages/smartlink/

It is a winmodem and have to find a driver that will work in linux. There is an UBUNTU folder and there may be a driver that would work.

I am really new to Linux and have not learned how to compile the source program yet.
 
So now you have 2 of 3 info (port 0x7800  irq 16) that the computer told you about  your modem.

Now to find which ttyS# your computer sees it at. Then setserial will tie everything together.

Wonder if there is anyone out there who has an already compiled driver for your modem.

---

### Post by IusedTObeSOMEONEelse on 2007-08-31
> **funsport said:**
> Hi Mustang,
    Barttender highlighted your modem.
    I did a search on your modem, and found this link.

linmodems.technion.ac.il/packages/smartlink/

It is a winmodem and have to find a driver that will work in linux. There is an UBUNTU folder and there may be a driver that would work.

I am really new to Linux and have not learned how to compile the source program yet.
 
So now you have 2 of 3 info (port 0x7800  irq 16) that the computer told you about  your modem.

Now to find which ttyS# your computer sees it at. Then setserial will tie everything together.

Wonder if there is anyone out there who has an already compiled driver for your modem.
Thanks for all the input. Still struggling with it. 
Clear Wire has come into area where I am moving and they are a wireless deal. Any one know if it will work with Linux? $19.95 for 3 months then $29.95 after

---

### Post by yellowbread on 2007-09-01
Just wanted to say thanks to funsport for the detailed instructions. I followed them exactly with the exception of using gnome ppp instead of kppp, and everything worked like a charm.
I also am using a USR 5610B and peoplepc for the ISP, so yes, peoplepc is not as truculent towards ubuntu as has been thought.

---

