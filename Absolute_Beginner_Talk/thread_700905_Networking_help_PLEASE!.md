---
title: "Networking help PLEASE!"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-02-18
First of all Hello...

I was hoping that someone can help me here...im in some network dilemma and i know by the time this is solved ill relize that it was easy in the first place i just didt know what to do. But back to the point, when i have a wired connection...i can connect and go surf the net :) But then when i try to connect to my wireless internet...without a card it fails :( ( connecting using my wifi)...ive tried the trouble shooting and no luck...my ESSID is broad casted...its not hidden...and the MAC address is already in the router...

Heres what i get for the following:
 
Device Recognition- Atheros Hardware Layer (HAL) enable and in use 

Checked for the driver- ```
 xtwoface@xtwoface:~$ sudo lshw -class network
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:ca:6c:04
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:73:6c:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
xtwoface@xtwoface:~$ 
 [/ code]

Check for a connection to the router- [code] xtwoface@xtwoface:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Joe's"  Nickname:"Joe's"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:12181  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and in my 

Windows Wirless Networking Driver (NDISWrapper)- i have the net5211 driver installed and it is present.


Does anyone have any suggestions to what i should be doing...or if im even on the right track...
PLEASE help...i greatly appreciate it!

---

### Post by spiderbatdad on 2008-02-18
you're very much on the right track and it looks like it should be working. Have you enabled roaming mode in your wireless connection manual configuration?

---

### Post by kaginken on 2008-02-18
You mentioned that you have the " MAC address in the router".  Are you filtering MAC address's?

If you're using encrypted wireless - try connecting w/o encryption first.  If you can, then that will narrow down the problem to your encryption.

Basically what I'm getting to is - open the router up wide open first.  Turn off mac address filtering if you are doing that, turn off encryption, etc.  THEN try it.  THEN start locking it back down, one thing at a time.

Also, for the record, I used to do a lot of that extra security stuff on my wireless, but now i just use the encryption.  Anyone that wants to can sniff out your SSID weather or not you're broadcasting it, and anyone that knows how can spoof a MAC addy.  So - why make it difficult for yourself - unless you've got, say, KFC's secret recipe on one of your computers or something, chances are nobody will be trying that hard to break in.  I only use the encryption now, to keep the honest people out.  That's just my opinion, I could be wrong!  :)

---

### Post by wankel on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/185331](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/185331) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Are you quite sure it actually is an AR5006EG?

I got a laptop with such ('7) a card in it, and I replaced it with another solution. My laptop is a shiny (yuck.. don't need a mirror as screen) Acer.

Back then I spend weeks on it, learned a lot, but did not get it working. Not to put you down, of course: maybe things changed since November last year.

The problem with the 5006/5007 emerged after Atheros forgot to change the PCI ID of their new chip combination or something.

There is a bug filed for this chipset on launchpad, I can not find the bug I found before at the moment.

Having a look at
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ar5006eg&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ar5006eg&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

I found a possible solution ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/185331):](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/185331):)


>  usr wrote on 2008-01-26:  (permalink)  
With NDISwrapper I can use Wi-Fi in Kubuntu 7.10 with this steps:
   1. Download the last version of the driver for Windows XP: azurewave_780_wlan_xp_nb.zip ([http://global.msi.com.tw/index.php?func=driverfile&dno=5637&i=1](http://global.msi.com.tw/index.php?func=driverfile&dno=5637&i=1))
    2. K Menu&#8211;> Run command... &#8211;> kcontrol &#8211;> System administration &#8211;> Restricted manager &#8211;> Root mode &#8211;> Disable the checkbox: "Atheros Harware Access Layer (HAL)" &#8211;> OK
    3. K Menu &#8211;> Run command&#8230; &#8211;> konsole &#8211;> sudo -s &#8211;> rmmod ath_pci &#8211;> echo &#8220;blacklist ath_pci&#8221; >> /etc/modprobe.d/blacklist
    4. Restart the system
    5. K Menu &#8211;> Run command&#8230; &#8211;> konsole &#8211;> sudo -s &#8211;> aptitude update &#8211;> aptitude install ndiswrapper-common ndiswrapper-utils-1.9
    6. Extract downloaded files in steep one and go to "ndis5" directory &#8211;> Settings &#8211;> Open terminal &#8211;> sudo -s &#8211;> ndiswrapper -i net5211.inf &#8211;> ndiswrapper -m &#8211;> modprobe ndiswrapper &#8211;> echo &#8220;ndiswrapper&#8221; >> /etc/modules
    7. Restart the system

Sorry not to be of any more help. Good luck anyway!

---

### Post by Lisa Y on 2008-02-19
THANK YOU ALL SOOO MUCH FOR HELPING ME!!!!!!!!!!

its working now...and im SOO happy!!!

thank you guys!

---

