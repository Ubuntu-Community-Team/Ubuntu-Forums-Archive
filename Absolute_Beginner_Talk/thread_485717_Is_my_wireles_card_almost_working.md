---
title: "Is my wireles card almost working"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-06-27
I could really do with some real help. For almost a week I've been trying to get my Belkin laptop card to communicate with the Belkin modem router connected to my desktop. 

I think I may be somewhere close  but nothing I do will allows the laptop wireless card  to communicate ( ie no lights are on) So far the laptop card seems to be recognised, as I can see it in networking connection properties as (ra0) I also have a network connection Ra0 icon in the taskbar with another network connection Ra0  icon, partly coloured yellow next to it.  

If I click on this yellow icon a window opens with the name raO and under "Activity" I have the following information:

Received packets (0.0b)
Sent 50594 packets (3.0mb) 

The signal strength bar below this is blank ie no activity in it.

The chipset for the Belkin laptop network card is Ralink 2500 and the laptop network card is a Belkin F5D7010. the The modem router is a Belkin ADSL wireless G   model F5D7632-4 

Am I anywhere near being connected?

---

### Post by overdrank on 2007-06-27
> **a.v.l said:**
> I could really do with some real help. For almost a week I've been trying to get my Belkin laptop card to communicate with the Belkin modem router connected to my desktop. 

I think I may be somewhere close  but nothing I do will allows the laptop wireless card  to communicate ( ie no lights are on) So far the laptop card seems to be recognised, as I can see it in networking connection properties as (ra0) I also have a network connection Ra0 icon in the taskbar with another network connection Ra0  icon, partly coloured yellow next to it.  

If I click on this yellow icon a window opens with the name raO and under "Activity" I have the following information:

Received packets (0.0b)
Sent 50594 packets (3.0mb) 

The signal strength bar below this is blank ie no activity in it.

The chipset for the Belkin laptop network card is Ralink 2500 and the laptop network card is a Belkin F5D7010. the The modem router is a Belkin ADSL wireless G   model F5D7632-4 

Am I anywhere near being connected?

Hi I am by no means a networking guy but have you seen this thread
[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)
It has helped some people with dapper. Hope this helps good luck! :D

---

### Post by aeiah on 2007-06-27
that howto is a method for ndiswrapper, which is fine, but there is a linux rt2500 driver which is very good i think. the one in ubuntu may be broken (their rt75 one is). there should be a howto on the forums for it. the actual driver can be downloaded from serialmonkey but its best to follow a howto for compiling and blacklisting etc

---

### Post by Austin_KW on 2007-06-27
The rt2500 installed with ubuntu is the legacy driver and works. You should not need to download a later driver  from serialmonkey but you can if you want. You should not need to blacklist anything unless you installed the ndiswrapper & windows driver.

Like the rt73 driver, the rt2500 does not support the wpa supplicant (uses its own internal wpa support) so to configure wpa support you will need to use the iwpriv command. It is easiest to configure the rt2500 in the /etc/network/interfaces.

FYI, my /etc/network/interfaces for a WPA-PSK (change for your config)
```
auto ra0
iface ra0 inet dhcp
####    pre-up iwpriv ra0 set CountryRegion=2 # For Europe (ch 1-13)
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set  WPAPSK="Txxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxcq2Yb"
    pre-up iwconfig ra0 essid MyNetName

```

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> The rt2500 installed with ubuntu is the legacy driver and works. You should not need to download a later driver  from serialmonkey but you can if you want. You should not need to blacklist anything unless you installed the ndiswrapper & windows driver.

Like the rt73 driver, the rt2500 does not support the wpa supplicant (uses its own internal wpa support) so to configure wpa support you will need to use the iwpriv command. It is easiest to configure the rt2500 in the /etc/network/interfaces.

FYI, my /etc/network/interfaces for a WPA-PSK (change for your config)
```
auto ra0
iface ra0 inet dhcp
####    pre-up iwpriv ra0 set CountryRegion=2 # For Europe (ch 1-13)
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set  WPAPSK="Txxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxcq2Yb"
    pre-up iwconfig ra0 essid MyNetName

```

Thank you for this, it looks  like what I might need. Please excuse my question, but which parts of the above will I need to change for my own config, I'm afraid this is new to me and I'm struggling a bit.   I'm in the UK and  I notice there are two entries in the above for.  

" pre-up iwconfig ra0 essid MyNetName"

Should this be and do I insert my ssid name in place of Mynetname? 

 I'm guessing "The WPAPSK=" should be changed for my own WPAPSK?

Should I change anything else? Much appreciate this help.

---

### Post by Austin_KW on 2007-06-27
Yes if you are using WPA just replace Mynetname with your ssid and set for your key. You may also want to uncomment the region code, use "2" for the UK which is channels 1-13

It should then work on boot.

To test after making the changes (without rebooting)
sudo ifup --f ra0

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> The rt2500 installed with ubuntu is the legacy driver and works. You should not need to download a later driver  from serialmonkey but you can if you want. You should not need to blacklist anything unless you installed the ndiswrapper & windows driver.

Like the rt73 driver, the rt2500 does not support the wpa supplicant (uses its own internal wpa support) so to configure wpa support you will need to use the iwpriv command. It is easiest to configure the rt2500 in the /etc/network/interfaces.

FYI, my /etc/network/interfaces for a WPA-PSK (change for your config)
```
auto ra0
iface ra0 inet dhcp
####    pre-up iwpriv ra0 set CountryRegion=2 # For Europe (ch 1-13)
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetName
    pre-up iwpriv ra0 set  WPAPSK="Txxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxcq2Yb"
    pre-up iwconfig ra0 essid MyNetName

```



I seem to have not got something right with this command.  Can you please take a look at the changes I've made for my system, The country code in particular  may have not been edited correctly. The following is how I've edited you command above but when I enter this into the terminal I get a message saying " cannot find this command.

auto ra0
iface ra0 inet dhcp
####    pre-up iwpriv ra0 =2
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid xxxxxxxxxxxxxxxxxxxxxxmyssidkey  
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid xxxxxxxxxxxxxxxxxxxxxxmyssidkey
    pre-up iwpriv ra0 set  WPAPSK=xxxxxxxxxxxxxxxxxxxxxxmywpa-psk key
    pre-up iwconfig ra0 essid xxxxxxxxxxxxxxxxxxxxxxmyssidkey

---

### Post by Austin_KW on 2007-06-27
The country code line should be;
```
pre-up iwpriv ra0 set CountryRegion=2 
```

If you still have problems post your actual /etc/network/interfaces (without the xxx obscuration), you can always change your keys later.

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> The country code line should be;
```
pre-up iwpriv ra0 set CountryRegion=2 
```

If you still have problems post your actual /etc/network/interfaces (without the xxx obscuration), you can always change your keys later.

Many thanks, I'll try later.

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> The country code line should be;
```
pre-up iwpriv ra0 set CountryRegion=2 
```

If you still have problems post your actual /etc/network/interfaces (without the xxx obscuration), you can always change your keys later.

As it happen I had some problems with Dapper running extremely slow on this laptop so I've installed Xubuntu instead. 

I then ran the command in terminal again and get the following, which does nothing at present, what might I be doing wrong? Below is a copy of the terminal result.  Can you help further?

auto ra0
Bash: auto command not fond
iface ra0 inet dhcp
####    pre-up iwpriv ra0 set CountryRegion=2
    pre-up ifconfig ra0 up
bash:pre-up command not found
    pre-up iwconfig ra0 mode managed
bash:pre-up command not found
    pre-up iwconfig ra0 essid xxxxxxxxxxmyssidnumber
bash:pre-up command not found
    pre-up iwpriv ra0 set EncrypType=TKIP
bash:pre-up command not found
    pre-up iwpriv ra0 set AuthMode=WPAPSK
bash:pre-up command not found
    pre-up iwconfig ra0 essid myssidnumberxxxxxxxxxx
bash:pre-up command not found
    pre-up iwpriv ra0 set  WPAPSK=myWPAPSKnumberxxxxxx
bash:pre-up command not found
    pre-up iwconfig ra0 essid myssidnumberxxxxxxxxxx
bash:pre-up command not found

---

### Post by Austin_KW on 2007-06-27
Ok, these are not terminal commands, they are configuration commands that need to be added to /etc/network/interfaces. Use the command "gksudo gedit /etc/network/interfaces" in a terminal, add the configuration as a single block. Then save and exit.

Then run "sudo ifup --f ra0"

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> Ok, these are not terminal commands, they are configuration commands that need to be added to /etc/network/interfaces. Use the command "gksudo gedit /etc/network/interfaces" in a terminal, add the configuration as a single block. Then save and exit.

Then run "sudo ifup --f ra0"


This was the result after entering the first command above.

$ gksudo gedit /etc/network/interfaces
sudo: gedit: command not found

Can you advise further please?

---

### Post by a.v.l on 2007-06-27
> **Austin_KW said:**
> Ok, these are not terminal commands, they are configuration commands that need to be added to /etc/network/interfaces. Use the command "gksudo gedit /etc/network/interfaces" in a terminal, add the configuration as a single block. Then save and exit.

Then run "sudo ifup --f ra0"



OK I've run the second command in Terminal and this was the result if it helps.


$ sudo ifup --f ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:11:50:65:9a:5b
Sending on   LPF/ra0/00:11:50:65:9a:5b
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Austin_KW on 2007-06-27
> **a.v.l said:**
> This was the result after entering the first command above.

$ gksudo gedit /etc/network/interfaces
sudo: gedit: command not found

Can you advise further please?

Sorry not paying attention, try "sudo nano /etc/network/interfaces"

the ifup will not work until you set the config in /etc/network/interfaces"

---

### Post by a.v.l on 2007-06-28
> **Austin_KW said:**
> Sorry not paying attention, try "sudo nano /etc/network/interfaces"

the ifup will not work until you set the config in /etc/network/interfaces"

I'm afraid I have no good news to report. Doing as you suggest hasn't improved matters for me. I did the sudo nano /etc/network/interfaces command which gave me a list of things which I tried to save in  /etc/network/interfaces but it seems that information is already there because when trying to save I was asked if I want to replace what is already there.

---

### Post by Austin_KW on 2007-06-29
Yes you are editing/changing an existing file, so you may have to confirm the changes when you exit with ctrl-X

---

### Post by a.v.l on 2007-06-29
> **Austin_KW said:**
> Yes you are editing/changing an existing file, so you may have to confirm the changes when you exit with ctrl-X

When I select yes to "save changes to interface"   I get and error message which says
"Cannot open file to write"

---

