---
title: "Help with wireless internet, was working but stopped"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by AmazingJustin on 2007-08-02
Hi everyone.  I got my wireless to work on Ubuntu after help from you guys.  I use Wicd as my wireless manager and have ndiswrapper.  When I do iwconfig I get this:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate=54 Mb/s Tx-Power:25 dBm
RTS thr=2347 B Fragment thr=2346 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Any suggestions?  I know next to nothing about Linux.

---

### Post by milosz.galazka on 2007-08-02
Hello,

If you wish to use wicd then run command in your desktop environment (like gnome, kde,...)

sudo /opt/wicd/gui.py

and choose network and configure its properties, that's all :)

There are other tools like wlassistant (wireless assistant). I am using knetworkmanager.

If you wish to do it fast for testing and you are using WPA2 for encryption you can do following steps:
1. Run wpa_passphrase with network name as parameter, like

wpa_passphrase MyHomeNetwork

execute and then enter password, you will get something like this:
milosz@bluebird:~$ wpa_passphrase MyHomeNetwork
# reading passphrase from stdin
testpassword
network={
        ssid="MyHomeNetwork"
        #psk="testpassword"
        psk=6aa1356cd8c026ad9e72f1a375547f8e8a34a40ff52d8c23d31033a6f60efd69
}

2. Then copy part

network={
        ssid="MyHomeNetwork"
        #psk="testpassword"
        psk=6aa1356cd8c026ad9e72f1a375547f8e8a34a40ff52d8c23d31033a6f60efd69
}

to file like test.conf

3. Run command

sudo wpa_supplicant  -Dndis -ieth1 -c/path/to/test.conf

4. Run dhcp client
sudo dhclient eth1    

5. Everything should be working now :)

---

### Post by imdano on 2007-08-02
That iwconfig print out shows that you aren't associated with any access point.  Are there networks in range?  Does wicd try to connect to a wireless network but fail, or does it not see any?

---

### Post by AmazingJustin on 2007-08-02
I'm using WEP encryption.  I can't detect any wireless connections for some reason.  I used to be able to detect a couple.

---

### Post by milosz.galazka on 2007-08-02
If *iwlist eth1 scan* isn't showing anything then maybe someone else will know answer as I never encountered  such problem

---

### Post by AmazingJustin on 2007-08-05
It is telling me no scan results.  Suggestions?

---

### Post by odin1965 on 2007-08-07
My wireless has stopped working in Fiesty as well. I am on  a Dell 1520 laptop. My wireless light flashes very quickly and network manager says it is trying to connect to the access point then it times out. While the light is flashing, iwlist eth1 scan gives "no scan results". If I go to manual configuration and disable the wireless connection, the light stops flashing and iwlist eth1 scan finds the access point.

I have tried Wicd and Wifi Radar and neither work either. I have removed the security from my access point and still no go. I have been reading every suggestion on these forums for the last few days and can not get anything to work. The driver is loaded and working and I am able to see networks in range, but cannot connect. 

I am still researching and trying various solutions. Anybody else have similar symptoms with the wireless light flashing very quickly?

---

