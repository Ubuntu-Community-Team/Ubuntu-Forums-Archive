---
title: "Wireless Internet packages were probably changed"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by gumpontheweb on 2008-02-01
Everything worked fine until one day. My brother installed adept and messed up the desktop. After trying to fix it I got everything to work again. I used synaptic and dselect to remove adept and possibly needed stuff. After removing adept the desktop never went back to normal.
While trying to get back to normal we noticed that you couldn't open file folders graphically, just in a terminal. The source list was erased in dselect which caused TONS of trouble for myself who doesn't know much.
Now after playing with ifup to get an internet connection over a wire. I figurd it out and 
sudo apt-get ubuntu-desktop.
After that is where I am now. I can connect with the laptop now over the wire but not over the wireless router.
The network manager looks different. It isn't the 2 comets. Instead it is a blue ball.
I can find networks. so I know that it is enabled but I still can't connect and get to the web.
I dont know if I deleted the driver or not? I don't think it would find networs names if it didn't work at all?
Now, I can cut & copy the outputs which I recently couldn't do.
The problem is bigger than just hooking up the wireless. Remember that it just worked fine.
Are The 2 comet icons another network manager besides the nm-applet? If that's what I even have?
Help me get the 2 comets again!
When I finally fixed the desktop by getting the ubuntu-desktop, when I opened firfox it brough up the familiar box to connect the first and only time. Since then I haven't seen the same login box to put in the lan password 
I just read how to check and I did all the iwconfig commands and didn't get any errors.
how should I get back the original software from the net. My cd-drive that I used to install is now broken so that isn't an option. I have tried to go through the wireless troubleshooting but it dont help. I've tried it all.

---

### Post by lswest on 2008-02-01
you can try setting it up with ```
sudo iwconfig [device name;e.g. wlan0/eth1] essid [ESSID of wlan] key [hex key, for ascii append "s:" before the key]
sudo dhclient [device name]
``` ? and to explain the commands: sudo iwconfig=run iwconfig as root, the device name tells it which device to configure, the essid command tells it the next string is the name of the wireless, the key is required to connect (if you have a key on your wlan), and the second line is another command, which requests an IP for your card from the dhcp server of your router.

---

### Post by jan quark on 2008-02-01
what is in your intefaces file ?
```
sudo gedit /etc/network/interfaces
```

---

### Post by gumpontheweb on 2008-02-01
> **jan quark said:**
> what is in your intefaces file ?
```
sudo gedit /etc/network/interfaces
```
```
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-key 5555555555555555555555555A
wireless-essid m



iface eth0 inet dhcp



auto eth1

auto eth0
```
i might go to sleep soon, should I make a new thread tomorrow?

---

### Post by jan quark on 2008-02-01
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#config](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#config)


it is said that 
> Be sure to list your Ethernet devices in order: lo, eth0, eth1, and so forth. They will be started in the order listed.
[http://www.linuxplanet.com/linuxplanet/tutorials/5736/3/](http://www.linuxplanet.com/linuxplanet/tutorials/5736/3/)

just giving some food for thought

---

### Post by thesoothsayer on 2008-02-01
I just tried my wireless after not using it for a while and I found a problem. Wired is normally eth0 and wireless is normally eth1 for my laptop.

I set the essid and connected to the wireless router. I then used "dhclient eth1" to obtain an address from the wireless router(AP) and got an IP like 192.168.1.x (the router/AP is 192.168.1.1). But when I tried to ping the router, it gave a "sendmsg" error for the ping.

So, I decided to use my wired connection to connect to the router and I configured the IP address to 192.168.1.y. However, before I connected using the physical cable, I tried a "ping 192.168.1.1 -I eth0" and it managed to ping! Seems that while ifconfig shows that wireless is eth1 and dhclient can use it to obtain an IP, there's some confusion somewhere because ping and other applications can't connect using eth1.


Edit: Looks like it was caused by firestarter. I removed it and it's working now.

---

### Post by gumpontheweb on 2008-02-03
> **thesoothsayer said:**
> I just tried my wireless after not using it for a while and I found a problem. Wired is normally eth0 and wireless is normally eth1 for my laptop.

I set the essid and connected to the wireless router. I then used "dhclient eth1" to obtain an address from the wireless router(AP) and got an IP like 192.168.1.x (the router/AP is 192.168.1.1). But when I tried to ping the router, it gave a "sendmsg" error for the ping.

So, I decided to use my wired connection to connect to the router and I configured the IP address to 192.168.1.y. However, before I connected using the physical cable, I tried a "ping 192.168.1.1 -I eth0" and it managed to ping! Seems that while ifconfig shows that wireless is eth1 and dhclient can use it to obtain an IP, there's some confusion somewhere because ping and other applications can't connect using eth1.[B][B][I][SIZE="2"]
Edit: Looks like it was caused by firestarter. I removed it and it's working now[/SIZE][/I][/B][/B].
I have firestarter installed and might have some simplistic ideas.(please remember that I have minimal knowledge of "this stuff")
After installing firestarter, I changed some of the settings in the process of getting the wireless to work. Something I did while trying to get the wireless card to pick up the internet, which is from this post: 
please post the results of the following terminal commands
Code:
```
iwconfig
```
Code:
```
ifconfig
```
Code:
```
lspci
```
Code:
```
sudo iwlist scan
```
__________________

Those commands & the  "  ifup eth0   "  command to get my wired port working. I just guessed it was that, after *reading a bunch of threads.* That's the trick!;-)
I have to restart every time I make any changes to my network also. If I don't, no connect. I also had to play around with the packages. First I was trying to get back my 2 comets for an icon. Really to get my first config back.
During that process I have found K... programs are not what I wanted. If I run any, BEFORE connecting, the connection attempts fail. It will show the lans, b ut won't ever connect.
I have got the wireless to work but I still don't have my two comets that Were in the Notification area.
What is the best LAN sniffer and other LAN tools, like nm-applet? 
KWifi Manager is the only LAN "sniffer" or graph maker I know of. If I run it then I can't get to the net.
what network graphing tool or compatible program works best with ubuntu?
what tools for network are best?

---

