---
title: "How to use Road Runner with ubuntu Feisty"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by kenny1948 on 2007-07-24
OK,
I know this is reduntant. However I am at wits end. I am new to ubuntu. I had it running for about a month and everything was perfect. I was using DSL to connect to the internet. Then we had a thunder storm ( here in Tampa that's an every day event during summer ) unfortunately it fried my DSL modem. When I got a new one and installed it I got this message "unsupported operating system, you must install Windows or MacOs"  When I tried using firefox I got a "this is a vin file" message when I tried to enter an address. I really do not know what this means, other than I cannot connect.

I called Verizon from whom I get my DSL. They informed me that " you cannot use Linux, period with Verizon DSL"  I called five different times each time asking to speak with someone who knew what the hell they were talking about. I got the same answer every time, including from two supervisors. Needless to say they were very rude and not helpful. 

So I switched to Broadband through Bright House networks. I am supposed to have Road Runner, but cannot connect using ubuntu.  I have a connection when I switch to WindowsXp which I have also on my running on my computer. I really want to keep using ubuntu, but cannot find out how to set it up. Their tech support does not support Linux. However twp of their techs said "yes you can use Linux" They could not however tell me how to set it up. They said it is possible but nobody there knew anything about Linux.

So now I'm stuck posting this using Windows!  Please someone help. My modem is an ARRIS Touchstone model number TM502G/H 

Can anyone help me. Please!

---

### Post by Al3xK3aton on 2007-07-24
Don't use DSL, use fiber optics.

---

### Post by deadlikeoscar on 2007-07-24
There is nothing to setup if you are using a wired cable connection with no router. Try opening a terminal and typing ```
ifconfig
``` and copy and paste what it says. You can also try typing ```
dhclient eth0
``` if it is a pain in the butt to post on the forums every time you try something.

*edit* on second thought there may be something you need to change if you switched from DSL to cable. Perhaps under System-->Administration-->Network. Make sure that there is a checkmark next to Wired Connection and that it says dhcp for the address. I've always used Cable for broadband so I have little experience with DSL.

---

### Post by delacerda on 2007-07-24
I'mm in Orlando and I love those storms! I have Brighhouse and use a router. It just makes connecting easier, plus I have several computers. You shouldn't have *any* problems connecting to the Internet using your cable modem. After you have your Ethernet adapter set up to use DHCP, disconnect the power from your modem, and turn off your PC. After about a minute or two, power on the modem, then boot the PC. You should be online after doing this.

---

### Post by Nythain on 2007-07-24
if you could at all post your /etc/network/interfaces file that might be a little helpfull also possibly

---

### Post by whorton on 2007-07-24
You should have been able to use any OS with a DSL or Cable connection. When they say it is unsupported they normally expect user to install their 3rd party crap to manage the WAN connection. Remember ISP provider tech support is not free thinking they go by a script. If your question is not in their scripting its unsupported.

---

### Post by kenny1948 on 2007-07-27
OK,
Here is the ipconfig readout: ( from windows xp)

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Owner>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:                                   Arris Telephony Modem

        Connection-specific DNS Suffix  . : tampabay.rr.com
        IP Address. . . . . . . . . . . . : 70.126.19.144
        Subnet Mask . . . . . . . . . . . : 255.255.254.0
        Default Gateway . . . . . . . . . : 70.126.18.1

Ethernet adapter Local Area Connection 2:                                 My D-Link adapter

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.18.152
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

C:\Documents and Settings\Owner>

I am using Road Runner with an  Arris Touchstone TM502G/H Telephony Modem
It only seems to work with a usb cable. I tried disconnecting the cable and I had no connection.

I also have installed a D-Link DFE-530TX+ fast ethernet adapter
My computer says it is enabled, but it is not receiveing anything
It is set up for DHCP do I need to enter a static IP address?

I have to type the one I got using Feisty:

ifconfig
eth0          Link encap: Ethernet  HWaddr  00:11:11:5B:B5:02
                 UP BROADCAST MULTICAST  MTU:1500  Metric:1
                 RX  packets:0  errors:0  dropped:0  overruns:0  frame:0
                 TX  packets:0  errors:0  dropped:0  overruns:0  carrier:0
                 collisions:0 txqueuelen:1000
                 RX  bytes:0  (0.0 b )   TX bytes:0  (0.0 )
eth2         Link encap:Ethernet     HWaddr  00:19:5B:72:BC:55
                UP BROADCAST MULTICAST   MTU:1500   Metric:1
                RX packets:0  errors:0  dropped:0  overruns:0  frame:0
                TX packets:0  errors:0  dripped:0  overruns:0  carrier:0
                collisions:0  txqueuulen:1000
                RX bytes:0  (0.0 b )    TX bytes:0  (0.0 b )
                Interrupt:20  Base address: 0xd800

lo             Link encap: Local  Loopback
               inet  addr: 127:0.0.1   Mask:255:0.0.0
               inet6 addr:  : :1/128  Scope:Host
               UP  LOOPBACK  RUNNING   MTU:16436   Metric: 1
               RX  packets:2  errors: 0  dropped: 0  overruns: 0  frame: 0
               TX Packets:2  errors: 0  dropped: 0  overruns: 0  carrier: 0
               collisions: 0  txqueuelen: 0
               RX  bytes:100  (100.0 b )    TX  bytes: 100  (100.0 b )

 does this give you any information---I really don't understand it.:confused:

---

