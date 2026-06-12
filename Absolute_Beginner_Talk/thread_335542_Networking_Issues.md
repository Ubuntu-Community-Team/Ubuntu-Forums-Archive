---
title: "Networking Issues"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tgdrums1990 on 2007-01-10
Hello all. I am very new to Linux. I am running Ubuntu 6.06 Desktop Edition on a HP Pavilion ZE4500 Notebook that is running a AMD  Athalon +2500. Anyways. I am having networking troubles. 
After instalation of Ubuntu I treid to set up my wireless card to pick up my wirless network. I dont know if it detected a wireless metwork or not. I did not get a pop of notifacation saying it tried to connect. Under the device settings I set the WEP key to hexidecimal and enterd my WEP key in. I then enabled the device and hit OK and closed the window. I then went and tried to open my Web browser. No internet. So I then went back and checked my device settings, it said the device was not active. So I tried it a few mroe times and gave up. 
I then went to my basment and used my ethernet cable and hooked it up to our network. Still no internet. At the top where the bar is it gave me symbol that shows I have a conection error. 
I left my cable plugged in and went back to the device properties. I once agin told my wirless card to activate. And then I got internet. But after unplugging my cable I lost internet. So im lost. 
Please help. You can contact me later tonight through IM around 9pm eastern time zone. My screen names are AIM:tgdrums1990, YAHOO:tgdrums1990, MSN:tgdrums1990@hotmail.com.  Or you can post a message back here. I prefer to IM tho. Thanks in advance.

---

### Post by riven0 on 2007-01-10
Alright, first you'll want to download network-manager. So when your connected to the internet, do:

> sudo apt-get install network-manager

Or do it through Synpatic, if you prefer. Then try:

> iwconfig

to see if that brings you a working wireless connection.

---

### Post by tgdrums1990 on 2007-01-10
Okay well I ran the first option and it said that everything is already updated. I ran the second option and here is what I got...
trevor@tl1:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

trevor@tl1:~$
trevor@tl1:~$


Where do I go from here? I know the Router is running.

---

### Post by doubled on 2007-01-14
> **tgdrums1990 said:**
> Okay well I ran the first option and it said that everything is already updated. I ran the second option and here is what I got...
trevor@tl1:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

trevor@tl1:~$
trevor@tl1:~$


Where do I go from here? I know the Router is running.

After several tries at this issue, I have stumbled upon a thread at
[www.ubuntuforums.org/showthread.php?t=12045](www.ubuntuforums.org/showthread.php?t=12045)
that had one piece of information in the October 7, 2005, note by andersi which unlocked it for me.

Here is my /etc/network/interfaces for eth1, my wireless card:

iface eth1 inet dhcp
wireless-essid Name_of_Wireless_Network
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-channel 6
wireless-mode managed

Note that it's 128-bit encryption!

Then, as andersi wrote, I issued this command: sudo ifdown eth1
followed by this command: sudo ifup eth1

That's what did it. I now have 128-bit encryption,at least, until my next reboot! ;) 

After the ifdown command, a line in the output indicated "Network unreachable"; however, after the ifup several lines were generated and the result was most satisfying.

So, I thank andersi and hope this helps others.

---

### Post by doubled on 2007-01-14
Sure enough, after reboot no joy. 

I did sudo ifdown eth1 and sudo ifup eth1 to no avail.

I did, in order:
sudo ifconfig eth1
sudo ifdown eth1
sudo ifup eth1

and the connection returned.

](*,) continues. I'll need to get a script writer to help.

---

### Post by doubled on 2007-01-14
I uninstalled WiFi Radar and installed "network-manager" and "network-manager-gnome" from synaptic package manager. Now the encrypted wireless connection occurs at boot.

---

