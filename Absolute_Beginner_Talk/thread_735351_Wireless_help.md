---
title: "Wireless help"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by guerilla on 2008-03-25
hello, 

i recently installed ubuntu 7.10, this was my first dip into linux and so im not really sure what i'm doing. 

i'm having problems connecting to my wireless network, the connection works in xp, but will not work on ubuntu. i'm quite sure that the drivers for the wireless dongle are installed correctly, but in the list of connections my network does not appear. im writing this on a laptop next to the ubuntu machine so i know the network is there. 

my router is a netgear dg834gt
my wireless adapter is a asus wl-167G

please help me get online, i was very excited about using linux for the first time but this has me pulling my hair out!

EDIT i can see other wireless networks to connect to but not my own

---

### Post by Helios38 on 2008-03-25
hello! you may need to install ndiswrapper. sometimes linux drivers just dont work right for the device  :(


im fairly sure ubuntu has a working one installed



first, gather the windows drivers for that dongle (it will be a .inf file)


then, in ubuntu, open a terminal window, and type


```
sudo apt-get install ndisgtk
```


this is a small GUI for ndiswrapper, allowing you to install windows wireless drivers to be used in ubuntu.



the GUI can be found in System > Administration > Windows Wireless Drivers (something like that, on xp atm)



then you can install the drivers from there, thats the easiest way i know for someone whos just dipping into ubuntu.

---

### Post by guerilla on 2008-03-25
okay tried the above and i get a message saying the package could not be found. im pretty sure the drivers are working fine because i can see other networks to connect to, my neighbours etc. but i cant see mine. ive googled this but it doesnt appear to be a common problem.

should i still install ndiswrapper? how would i do this without being connected to the internet?

---

### Post by nick_h on 2008-03-25
You might not have to use ndiswrapper.

The asus wl-167G is listed on the [WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) page.

I suggest you start the debugging process by looking at the output of the following commands:
```
lsusb
iwconfig
iwlist wlan0 scan
```

---

### Post by jan quark on 2008-03-25
you can also check if your drivers for your wlan device are installed with this command 
please post the output here:

```
sudo lshw -C network
```

---

### Post by guerilla on 2008-03-26
thanks for the help, i'll do this as soon as i can get back to the machine, i'm at work at the moment

---

### Post by guerilla on 2008-03-26
david@david-desktop:~$ lsusb
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 003: ID 062a:0102 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0b05:1706 ASUSTek Computer, Inc. 
Bus 001 Device 005: ID 07b8:e004 D-Link Corp. 
Bus 001 Device 001: ID 0000:0000  

david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-desktop:~$ iwlist wlan0 scan
wlan0     No scan results

david@david-desktop:~$ sudo lshw -C network
[sudo] password for david:
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:31:99:fc:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by guerilla on 2008-03-26
there you go guys hopefully you know what this means

---

### Post by forrestcupp on 2008-03-26
It appears that your wireless card is working.  

Do you have a wireless networking icon in your notification area?  It looks like 4 signal strength bars.  If so, click on it.  Your connection isn't listed?  Try clicking 'Connect to other Wireless Network...'  In that window try entering the name of your network and what kind of security it has and see if you can connect that way.

---

### Post by m60dude5 on 2008-03-26
Hi. I had the exact same problem. If you don't already have your SSID broadcasted, do so now. I did that and I was able to connect. Just click "connect to other wireless network" and type your SSID and your WPA key. Worked for me.

---

### Post by guerilla on 2008-03-26
i have a symbol that looks like two computers with a warning sign, near the clock, is this the notification area? when i click on this it shows somw wireless networks but not mine. when i click connect to other wireless network the symbol dissappears and then nothing happens.

i cant get the symbol back so i have to restart.

btw ssid is broadcasting and im using the 64bit version of ubuntu

---

### Post by guerilla on 2008-04-02
still need help with this. am afraid i may have to abandon ubuntu altogether, its not much use if i cant access the internet

---

### Post by nick_h on 2008-04-02
> i can see other networks to connect to, my neighbours etc.
If you can connect to your neighbour's router then your card must be working.  Is the security the same on the router you connect to as your own?  Perhaps temporarily removing security from your router would be a good idea as a test.

Have you looked in your log files to see if there are any errors?

---

### Post by Crafty Kisses on 2008-04-02
> **nick_h said:**
> If you can connect to your neighbour's router then your card must be working.  Is the security the same on the router you connect to as your own?  Perhaps temporarily removing security from your router would be a good idea as a test.

Have you looked in your log files to see if there are any errors?

Yeah, remove any encryption or ssh-keys or whatever kind of security you have on your router for the time being, just to test.

---

### Post by guerilla on 2008-04-28
gforgot about this post. this problem is solved, ubuntu didnt like my network being on channel 13,

---

