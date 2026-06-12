---
title: "help - Ad-Hoc Linux to Linux internet sharing"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Schinoble on 2007-10-08
Presently i am using windows XP as my main system and Ubuntu on the laptop to connect to  windows via adhoc to share the internet connect, using 

Linux to windows Ad-Hoc

sudo ifconfig ath0 down
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/init.d/networking stop
sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=adhoc
sudo iwconfig ath0 channel 2 
sudo iwconfig ath0 essid laptop
sudo iwconfig ra1 key s:12345

any help in tidying up the above would be appreciated. 

than once its connected running

sudo dhclient ath0

to try and get the Ad-Hoc linux to linux i'm using the following

the laptop is using an altheros card and the desktop is using the RT61 driver

i use this script on the main computer 

sudo ifconfig ra1 down
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/init.d/networking stop
sudo dhclient eth0
sudo iwconfig ra1 mode ad-hoc
sudo iwconfig ra1 channel 2 
sudo iwconfig ra1 essid laptop
sudo iwconfig ra1 key s:12345
sudo ifconfig ra1 up
sudo ifconfig ra1 192.168.0.1 netmask 255.255.255.0

and this script on the laptop 

sudo ifconfig ath0 down
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/init.d/networking stop
sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=adhoc
sudo ifconfig ath0 up
sudo iwconfig ath0 channel 2
sudo iwconfig ath0 key s:15243
sudo iwconfig ath0 essid laptop
sudo ifconfig ath0 192.168.0.2 netmask 255.255.255.0 

this is the sudo iwconfig result i get for the altheros card

ath0      IEEE 802.11g  ESSID:"laptop"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 02:16:E3:24:78:8E   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3135-3234-33   Security mode:restricted
          Power Management:off
          Link Quality=57/94  Signal level=-32 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and the sudo iwconfig result i get for the RT61 card

ra1       RT61 Wireless  ESSID:"laptop"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 02:16:E3:24:78:8E   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:3135-3234-33
          Link Quality=100/100  Signal level:-36 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

any ideas what i'm doing wrong, i cant seem to ping the other IP address from one comeputer to the other, thanks in advance for any help 

the next step would be to try and route the internet from one machine to the other, but presently i cant even get one to ping another :(

---

### Post by cubeplayr on 2007-12-31
I'm having a similar problem.  Can anyone help?

---

