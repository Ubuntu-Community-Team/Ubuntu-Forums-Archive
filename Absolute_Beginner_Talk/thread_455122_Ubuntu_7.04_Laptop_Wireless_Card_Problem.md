---
title: "Ubuntu 7.04 Laptop Wireless Card Problem"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by dbusse on 2007-05-26
I have installed Ubuntu 7.04 on my Toshiba Satellite A105-S4254 laptop.  The laptop contains a Intel Pro/Wireless 3945 Network card which has a restricted driver.

I checked the forum but was not able to find anything exactly like my problem.  Apologies if this turns out to be a duplicate post.

When I configure my wireless card under the Live CD, after several tries I got it to work.  So I installed Ubuntu on the system (dual boot with Windows XP).

After installation I was not able to get the wireless card to work after configuring it manually and entering my WEP password.  I repeated this several times just to be sure I had not fat-fingered the password.  No Joy.

The wired interface on my laptop works with no problem.  I used it to update Ubuntu, but the problem with the wireless card persists.

I discovered the following:

Under System->Administration->Network Tools, on the “Devices” tab, the Network Device drop-down has four devices: Loopback Interface, eht0 Interface (wired connection), eth1 interface and eth1:avahi interface.  The "eth1" interfaces appear to be the wireless card.

The eth1 has “Not Available” for all Interface Information.  Under IP Information it has one line, Protocol is IPv6, IP Address is fe80:218:deff:fe06:8065, Netmask is 64, Broadcast is blank, Scope is “link”.  Clicking on the Configure button results in a dialog where my ESSID, Wep Key type and password and configuration settings are shown correctly.

The eth1:avahi interface has Interface information all looking correct, Mac address, etc is right for my wireless card.  The IP Information also looks reasonable with protocol of IPv4 and valid IP addresses for IP Address, Netmask, and Broadcast. The scope column is blank.  But when I click on Configure, I get a dialog that says the interface does not exist!

My question is, since the eth1:avahi seems to have all the correct information, how can I use it to connect?  If this is some sort of device configuration error, and there should only be one eth1 interface, how do I fix it?

One more very strange observation.  I left the laptop running overnight.  When I looked at it in the morning, the wireless card was connected to my home network.  I had done nothing to it.  But rather than looking at Network Tools, I foolishly re-booted to see if it would re-connect.  No joy, back to square one.  Data on Network Tools dialog remains as I described above.

Any help would be appreciated!

---

### Post by Kobalt on 2007-05-26
Usually your card is set up easily, but you need to install linux-restricted-modules-`uname -r`. In a Terminal run the following command line (copy/paste it maybe) and if it's not installed already, install it. ```
sudo apt-get install linux-restricted-modules-`uname -r`
```You may need to reboot so that the changes take effect.

---

### Post by dbusse on 2007-05-26
Thanks very much for your suggestion.  I tried it, the command seem to run OK.  But it had no effect.  Wireless is still not working.

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

### Post by dbusse on 2007-05-27
I worked through the[ _wireless troubleshooting guide_]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw") and somewhere along the line the thing started working and has worked ever since.  I don't understand what exactly I did (which is frustrating) but it is working.

---

### Post by dbusse on 2007-05-31
To darwin_te

Your post is interesting, but I'm not quite sure what you are trying to tell me.

I am having trouble with the wireless card again.  It seems to work on boot sometimes and not at others.  There is some issue still unresolved.  Any help would be appreciated.

---

### Post by jvictor on 2007-06-03
I too found the same problem and reverted to 6.10. The networking thingy works if it likes to. I dont have the time to set it every now and then.. another thing is I don't find any great benefit of using 7.04 as long as I get back ports..

---

