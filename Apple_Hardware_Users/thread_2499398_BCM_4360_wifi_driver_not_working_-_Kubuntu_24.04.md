---
title: "BCM 4360 wifi driver not working - Kubuntu 24.04"
date: 2024-07-25
forum: Apple Hardware Users
---

### Post by im2fst4u on 2024-07-25
Hi there I got a 2015 macbook I'm trying to get kubuntu 24.04 to work properly. 
It has a BCM4360 dual band network adapter.

Trying it out from usb seemed okay, but I got no wifi capabilities. I tried every which way to install the drivers but no luck

I figured this might be because I hadn't done the full install yet. So I did that, worked, but with no toolbars in the corner to open up wifi for instance.
So I reinstalled and fixed that issue. 

I've been trying things like this:
[https://gist.github.com/torresashjian/e97d954c7f1554b6a017f07d69a66374](https://gist.github.com/torresashjian/e97d954c7f1554b6a017f07d69a66374)
But no luck. I use usb tethering for the downloads, but after reboot I still don't have any wifi networks pop up. 
I noticed that man_db  seems to be missing possibly? Not sure if it's related. I was noticing it while trying to get the drivers to work. 

The driver manager says the device is currently using an alternative driver for the network adapter.
"using dkms source for for the broadcom STA Wireless driver from broadcom-sta-dkms (proprietary)"

I'm about ready to give up on using ubuntu at this point...

---

### Post by tea for one on 2024-07-25
Have you seen this info:-
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by QIII on 2024-07-25
Moved to Apple Hardware Users

---

### Post by im2fst4u on 2024-10-15
So, here's the solution i found to this problem:
Basically, after doing everything in this post:

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I was able to see networks around me. I could connect to a wifi hotspot, but I could not connect to my home wifi. I figured out this was likely due to the home wifi being only wpa3 (Which I couldn't change to accept wpa2 due to the router not being in my hands to control)

After communicating with Copilot (which was more helpful than I anticipated) a solution was eventually reached, I'll try my best to detail it here:

I followed everything in the post above. This included the blacklisting.
my pci.id was 14e4-43a0, I  used the code below to figure this out: 

*lspci -nn -d 14e4:*

Next,

[I]uname -r

[/I]To check the kernel (uname was was 6.8.0-45)

[I]sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo apt-get install linux-firmware
dmesg | grep wlp3s0
[/I]
This is where things got interesting, my system read: "[COLOR=#282523][FONT=Ginto]dmesg: read kernel buffer failed: operation not permitted"
[/FONT][/COLOR]
So we removed the security restriction:
[I]
sudo sysctl -w kernel.dmesg_restrict=0
dmesg | grep wlp3s0[/I]

Ran into another error: "[        5.872018] wl 0000.03:00.0 wlp3s0: renamed from wlan0"
Checked the network manager logs:
[I]
sudo journalctl -u NetworkManager | grep wlp3s0
[/I]
Found that after showing copilot a picture of the logs it diagnosed that:

[COLOR=#000080]your device is trying to connect but is having trouble with the SSID not being found. This could indicate a few different issues:

Network Visibility: Ensure your WiFi network (SSID) is visible. Hidden networks can cause issues with automatic connections.

WPA3 Configuration: WPA3 can sometimes be finicky. Ensure your router is set to support WPA2/WPA3 mixed mode, which might help with compatibility.

Security Settings: Double-check the security settings and passwords for your network.

To narrow this down further, try creating a temporary WiFi hotspot on another device (like your phone) with simple WPA2 security and see if your laptop can connect to that. This will help identify if the issue is specific to WPA3.[/COLOR]

So after this I checked that I could use a wifi hotspot, and that I could do it after configuring the wifi security to WPA/WPA2 personal for the connection I was trying. This still didn't solve the issue with the home network. so next we updated the network manager to try and get updated wpa3 support. (at the time it was 1.46)

[I]sudo apt-get update
sudo apt-get install network-manager
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

network={
    ssid="yourSSID"
    psk="yourPassword"
    key_mgmt=WPA-EAP-SHA256
}[/I]

Ctrl + 0 
Enter
Ctrl + X
-modifying the supplicant and exiting nano. 

[I]sudo systemctl stop NetworkManager
sudo wpa_supplicant -B -i wlp3s0 -c /etc/wpa_supplicant/wpa_supplicant.conf
sudo dhclient wlp3s0[/I]

At this point the command for dhclient was not found so we installed it:[I]

sudo apt-get install isc-dhcp-client[/I]
*sudo dhclient wlp3s0*

At this point my terminal hung up, as in I could type in things, but pressing enter wouldn't execute a command. I would have to exit the terminal. (The process was still running at this point) Going back into the terminal I entered:
[I]
sudo pkill dhclient
sudo dhclient -r wlp3s0[/I]

The terminal told me a stale PID file was removed. This may have been what helped me. But when I would try this code again:
[I]
sudo dhclient wlp3s0[/I]

It would consistently hang and I would have to close the terminal. 
 For in the next step where Copilot was having me manually connect to my network (see what it said about that below) 
In order to do this I decided to turn on the network again so I could find what my ip address was:
[I]
sudo systemctl start NetworkManager[/I]

And somehow, instead of connecting to my usb tether, it caught and maintained a connection to my home network!!!
I didn't know what exactly solved the issue, but I can have a stable connection to my home network now. 
Hopefully this helps someone!!


(Code for manually connecting to network. This is just for reference in case someone needs it)
[I]sudo ifconfig wlp3s0 <your-ip-address> netmask <your-netmask>
sudo route add default gw <your-gateway-ip>
sudo nano /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
[/I]

---

