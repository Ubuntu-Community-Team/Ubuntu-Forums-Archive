---
title: "Ubuntu on wireless"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by sontek on 2005-05-23
I just completed an install of Ubuntu on my laptop. The laptop is an IBM Thinkpad R50. It was able to detect the network card but I was unable to connect to my schools network.  But I am able to connect to it through the windows configuration that my school had setup on it.   

Here are the settings I can see:
The WEP Key is provided for me automatically
Network Authentication: Open
Data Encryption: WEP
EAP Type: Protected EAP (PEAP) - EAP-MSChap v2


It is DHCP.  We login to the network through a radius server so i'd like to do that at sometime. (Not a big deal right now)




Here is the windows ipconfig /all for it



Windows IP Configuration



        Host Name . . . . . . . . . . . . : JANDERSON

        Primary Dns Suffix  . . . . . . . : Student.School.local

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : Student.School.local

                                            student.School.local

                                          School.local



Ethernet adapter Wireless Network Connection:



        Connection-specific DNS Suffix  . : Student.School.local

        Description . . . . . . . . . . . : 11a/b/g Wireless LAN Mini PCI Adapter

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 10.225.24.34

        Subnet Mask . . . . . . . . . . . : 255.255.252.0

        Default Gateway . . . . . . . . . : 10.225.24.1

        DHCP Server . . . . . . . . . . . : 10.245.27.15

        DNS Servers . . . . . . . . . . . : 10.245.27.3

                                            10.245.27.10

        Lease Obtained. . . . . . . . . . : Monday, May 23, 2005 9:41:17 AM

        Lease Expires . . . . . . . . . . : Monday, May 23, 2005 1:41:17 PM



Ethernet adapter Local Area Connection:



        Media State . . . . . . . . . . . : Media disconnected

        Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Mobile Connection





Plus any tools/config files that I need to set this up would be helpful since this is my first time using ubuntu.

---

### Post by Zelut on 2005-05-23
My best suggestion right now would be to search the forums for HOWTOs on setting up your wireless connection.  Wireless is still fairly new to the linux world & not 100% supported yet.  I think your chances are better with the hardware you have, but still not guaranteed.

Do a few searches & see if you can find any existing information.  I'm on different hardware so I had to go a different route to get it to work than you will I'm sure.

---

