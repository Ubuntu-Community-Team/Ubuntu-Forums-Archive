---
title: "No wireless in NetworkManager"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sorryjustme on 2007-02-06
I am using 6.06, and had managed to set up my wireless network at home to work beautifully using WEP encryption. On holiday, I wanted to connect to a WPA encrypted network, and with lots of problems, I did managed to finally, for a short while... I ended up editing /etc/network/interfaces and /etc/wpa_supplicant.conf files. 

Now that I am back at home, I have tried reconnecting back to my original settings, with no avail. I have tried the GUI Network settings (System>Admin>Network) and nothing happens, I have also tried rediting the above files, with no success as well...

In the past, I have tried using NetworkManager, but I have never been able to get the Wireless option... Even right clicking, doesn't give me the "enable wireless option". Does anyone have any suggestions? I have also tried Wifi-radar, but I can't seem to be able to configure this one correctly either...

Sorry for the longwinded post. Hope someone can help!

Cheers,

Sorryjustme

---

### Post by aseneca on 2007-02-06
I guess a good start would be start by posting some of your info....


What does iwconfig return?  iwlist scanning?  Are you using ndiswrapper functionality?

;) Thanks 

AS

---

### Post by sorryjustme on 2007-02-06
iwconfig gives me :
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

iwlist scanning gives me:
lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


I do believe I am using ndiswrapper. I have a broadcom 4306, which was a nightmare to set up initially. I used the bcm 43xx Howto to get it all up and running in the end.

Any thoughts?

---

### Post by aseneca on 2007-02-06
Hmm.. Could always try trust old iwconfig commands....

sudo iwconfig eth1 essid *********name of your wireless network*****
sudo iwconfig eth1 key **********your WEP key***********

see what happens...

;) broadcom isn't so bad to setup.. see what happens why you try that...

AS

---

### Post by casaschi on 2007-02-06
An option is to replace NetworkManager with another wifi manager, I've been successful with wifi-radar , it works in a different way than NetworkManager, but made my wifi working with WAP.

---

### Post by aseneca on 2007-02-06
An interesting discovery!

[http://ubuntuforums.org/showthread.php?t=31859](http://ubuntuforums.org/showthread.php?t=31859)

---

### Post by aseneca on 2007-02-06
Any luck?

[http://www.linuxquestions.org/questions/showthread.php?t=449116](http://www.linuxquestions.org/questions/showthread.php?t=449116)

AS

---

### Post by sorryjustme on 2007-02-06
sudo iwconfig eth1 myESSID gives me "Unrecognised wireless request "myESSID".

Should I be using quotation marks ?:confused: 

I have got rid of the WEP while I try to connect, and have just got an open network at the moment.

---

### Post by aseneca on 2007-02-06
sudo iwconfig eth1 essid *********name of your wireless network*****

aseneca@aseneca-laptop:~$ sudo iwconfig essid mynetworkrocks


Nope, no questions marks.  I initially posted incorrectly but I edited it.  Try again.

AS

---

### Post by aseneca on 2007-02-06
FYI too. It is reasonable to use MAC restriction on your router to only allow registered devices to access your network.  Use that and don't broadcast your network.  

Any luck?

AS

---

### Post by sorryjustme on 2007-02-06
ok, sudo iwconfig eth1 essid myESSID makes the wireless LED light up, but nothing happens. If I try to PING [www.yahoo.com](www.yahoo.com), it just comes back as unknown host.

---

### Post by sorryjustme on 2007-02-06
> **aseneca said:**
> FYI too. It is reasonable to use MAC restriction on your router to only allow registered devices to access your network.  Use that and don't broadcast your network.  

Any luck?

AS

I agree... Just at the moment, I want to just get my wireless back up and running then I can sort the rest out...

---

### Post by aseneca on 2007-02-06
aseneca@aseneca-laptop:~$ sudo dhclient

you also many need to disable your ethernet connection under system>administration>networking       to check your wireless connection.  Or if you're using dapper just change the default gateway 

;)
AS

shoot me an email here ( I think you can do that) and I'll send you my messenger contact information

---

### Post by sorryjustme on 2007-02-06
> **casaschi said:**
> An option is to replace NetworkManager with another wifi manager, I've been successful with wifi-radar , it works in a different way than NetworkManager, but made my wifi working with WAP.

As I said earlier on, I tried wifi-radar as well... It detects my network, and tries to connect to it,  but doesn't acquire an IP. I can't work out how to configure it properly.

---

### Post by sorryjustme on 2007-02-06
> **aseneca said:**
> aseneca@aseneca-laptop:~$ sudo dhclient

you also many need to disable your ethernet connection under system>administration>networking       to check your wireless connection.  Or if you're using dapper just change the default gateway 

;)
AS

shoot me an email here ( I think you can do that) and I'll send you my messenger contact information

Whether I do either of those things, I still don't seem to be able to connect to anything...
Your link to shoot the email didn't seem to work either... Or maybe I'm a little slow tonight?!

---

### Post by aseneca on 2007-02-06
aseneca@aseneca-laptop:~$ sudo dhclient

tries to obtain an ip from the router; two connections eg. an ethernet connection and a wireless connection both assigned by DHCP causes problems with EDGY.  Dapper has a configuration that allows you to specify the default gateway to avoid confusion (eg. which is the connection to the internet)

So, see if dhclient gets a connection.  We can troubleshoot from there.  Whats the output from dhclient in the terminal.

I thought that this forum allows emailing via username; it wasnt a link.

AS

---

### Post by sorryjustme on 2007-02-06
sudo dhclient gives me this:

[INDENT]Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:38:08:a9:6a
Sending on   LPF/eth0/00:14:38:08:a9:6a
Listening on LPF/eth1/00:90:4b:a6:3f:e7
Sending on   LPF/eth1/00:90:4b:a6:3f:e7
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7[/INDENT]

and carries on till I kill it....

---

### Post by aseneca on 2007-02-06
Look at this post.  

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

It details the installation of a 43xx broadcom card.  Scroll down once or twice to view the part about the wifi-radar.  

I can recall in the past having issues with this.  Remove that and  restart networking services

aseneca@aseneca-laptop:~$ sudo /etc/init.d/networking restart


Repost

AS

---

### Post by sorryjustme on 2007-02-06
removed wifi-radar, restarted networking, and still no connection with dhclient...

I am just wondering if I really messed up the networking files... 

The ones I changed were: /etc/network/interfaces and /etc/wpa_supplicant.conf . I also edited /etc/wpa_supplicant/wpa_supplicant.conf, as this is the one that wifi-radar was looking for.....

Have I mucked the whole thing up?

I think that  I have emailed you btw.....

Cheers!

---

### Post by aseneca on 2007-02-06
I got a message from you on MSN.  But I get this error when messaging back.

(16:24:08) Message could not be sent because an error with the switchboard occurred:

Do you remember changing anything with your IP address or DNS server(s) when you manually changed your network interfaces?

AS

---

