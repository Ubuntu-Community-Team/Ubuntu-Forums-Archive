---
title: "Problems with wlan ipw2200 wpa"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by doerum on 2007-01-08
Hi

I'm using edgy (and I’m a totally linux newbie), and have problems with the wlan connection on my laptop. My card is an Intel pro wireless 2200 bg.  I have tried several threads, but nothing seems to work. The wlan uses wpa, and dhcp. 

I have tried wifi radar, but there is no connect button. I have also tried network manager, but it hooked me up with my neighbours network (and that didn’t work either).  Should I update the ipw 2200 driver or use the default driver……? I have no idea what to do, please help. ](*,)

---

### Post by scrooge_74 on 2007-01-08
if you card is working and you can see the network, try for a moment to take down the security and see if you can connect.

Check this

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by dca on 2007-01-08
The ipw2200 worked out of the box on my Dell laptop on both 6.06LTS and 6.10...   I agree w/ the removing all security from your router and attempting to connect...

---

### Post by doerum on 2007-01-10
Hi again

Thank you for your help. I experimented with wpa, and searched forums etc.
I've finally got it working, with wpa_supplicant. I 'll add a link to it later on (don't have it on this computer). 

But i was wondering if you perhaps know how to make a start up script? So that wpa_supplicant starts automatically (spelling error?) when edgy stars?

best regards
Dørum:-D

---

### Post by wieman01 on 2007-01-10
Startup script as shown in the HOWTO in my signature. Give it a go. The correct wpa-driver for IPW2200 is "wext" (you'll know what I mean).

---

### Post by doerum on 2007-01-18
Thanks! I've got it working now.

---

### Post by doerum on 2007-01-20
By the way. Here's is how i got it working. I saved the file, but don't remember where i found it. Here goes (remember to use "sudo gedit" in the terminal before you modify any files):

HOWTO: IPW2200 WLAN under Edgy with WPA encryption 
After upgrading from Dapper to Edgy my wpa-encrypted WLAN-connection did not work anymore. So I was looking for HowTos on the Internet but none of them worked properly on my Acer TM800. So I figured the settings out on my own.

Here's what I did:

1)
Installation of Edgy (from the alternate CD)

2)
Modification of (use sudo and gedit) /etc/network/interfaces - eth1 is my IPW2200:
auto eth1
iface eth1 inet dhcp
(note that I'm using DHCP)

3)
Creation of a file named /etc/wpa_supplicant.conf with this content:
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
ssid="myessid"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
psk="mypsk"
}

4)
Reboot.

5)
Try if everything works with:
sudo wpa_supplicant -D wext -i eth1 -c /etc/wpa_supplicant.conf -w -dd

6)
If you're using dhcp, try "sudo dhclient eth1" and watch if you'll get an IP-Address.

7)
Create a start-script as described in other HowTo's.
(like here: [http://www.ubuntuforums.org/showthread.php?t=26623;](http://www.ubuntuforums.org/showthread.php?t=26623;) be sure to locate wpa_supplicant ... in my case it's in /sbin and not in /usr/sbin)
-------------------------------------------------------------------------

Only like to say that if you put the string in "/etc/network/interfaces" you will get an error if you try to reload the DHCP "sudo ifup -a --force"

I would go for a boot script in the /etc/init.d/your_own_script
And add it using
Code:

update-rc.d -f your_own_script start 40 S .

---

### Post by scrooge_74 on 2007-01-20
You should correct the use of "sudo gedit" for "gksudo gedit" it seems you could break things using just sudo in a GUI

---

### Post by brettr on 2007-01-21
Somebody correct me if i am wrong, but in edgy at least i did not think that you had to implement a startup script. I was recently playing around with wpa_supplicant, and it was integrated with "ifup <wireless_interface>". Assuming you put the correct lines in /etc/network/interfaces fle.

---

