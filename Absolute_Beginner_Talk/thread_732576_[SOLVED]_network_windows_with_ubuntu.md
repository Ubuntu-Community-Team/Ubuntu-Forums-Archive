---
title: "[SOLVED] network windows with ubuntu"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by neobuddha on 2008-03-23
I have been using ubuntu feisty fawn for several months now.I really love it.It is what I connect to the internet with .Ido this via dialup using gnome ppp.My wife has a desktop running windows xp because of online games that will only work on windows.I want to connect the windows computer to the internet through my ubuntu desktop via ethernet.Can anyone tell me how to acomplish this?

---

### Post by firstsky on 2008-03-23
Look at!

---

### Post by DaV|d on 2008-03-23
```
sudo apt-get install dnsmasq ipmasq firestarter
```
dnsmasq: DHCP and DNS server
ipmasq: sets up set up ip masquerading
firestarter: firewall
The firewall configuration wizard lets you choose your internet connected device (something like ppp0) and your network connected device (ethX). Set up those and you're done.

---

### Post by neobuddha on 2008-03-24
> **DaV|d said:**
> ```
sudo apt-get install dnsmasq ipmasq firestarter
```
dnsmasq: DHCP and DNS server
ipmasq: sets up set up ip masquerading
firestarter: firewall
The firewall configuration wizard lets you choose your internet connected device (something like ppp0) and your network connected device (ethX). Set up those and you're done.

Thank you for your reply. I ran the command that you suggested.But when I try to set the firestarter settings I get the message "The device eth0 is not ready.". Do you know how to resolve this? Thank you.

---

### Post by DaV|d on 2008-03-25
Check that the modem and all network hardware is connected and switched on.
[This]("http://www.techthrob.com/tech/firestarter.php") link should help you get started on configuring your firewall.

If you still are getting errors, could you please post the output of
```
ifconfig
```

---

### Post by neobuddha on 2008-03-25
> **DaV|d said:**
> Check that the modem and all network hardware is connected and switched on.
[This]("http://www.techthrob.com/tech/firestarter.php") link should help you get started on configuring your firewall.

If you still are getting errors, could you please post the output of
```
ifconfig
```


Here is the results of ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:40:CA:B1:A0:4C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38638 (37.7 KiB)  TX bytes:34578 (33.7 KiB)
          Interrupt:20 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:CA:B1:A0:4C  
          inet addr:169.254.7.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7640 (7.4 KiB)  TX bytes:7640 (7.4 KiB)



Bu t I have a more serious problem.Today when I tried to dial my ISP , it could not connect. I have been trying all day.I was able to connect by using gnome-ppp as root.But then my browser could not connect to any website I tried.I am writing this from my laptop.Can anyone help.

---

### Post by Iowan on 2008-03-25
I'm still a little confused as to why, but apparently Network Manager will activate only one interface at a time.  You might be able to re-activate your dial-up under the Manual network configuration icon in upper right corner.

---

### Post by DaV|d on 2008-03-25
Your ethernet connection doesn't seem to be configured. Go to System > Administration > Network and configure your lan interface. Set up a static ip and gateway address of 192.168.0.1, and a subnet mask of 255.255.255.0  

Also, please re-check the setup of your dial-up connection.

PS. are your computers connected together via a router? if not ensure that you are using a cross-over ethernet cable.

---

### Post by neobuddha on 2008-03-25
> **DaV|d said:**
> Your ethernet connection doesn't seem to be configured. Go to System > Administration > Network and configure your lan interface. Set up a static ip and gateway address of 192.168.0.1, and a subnet mask of 255.255.255.0  

Also, please re-check the setup of your dial-up connection.

PS. are your computers connected together via a router? if not ensure that you are using a cross-over ethernet cable.


I followed your suggestion but it didn't work. When it was set to dchp automatic,the taskbar icon said I had a wired connection.But the windows machine said that the other machine failed to give it a n ip adress.I could even browse the shared folder on the windows machine from my ubuntu machine.
Now it does not have a connection at all.
I am using a crossover ethernet cable.

I still can't use the internet.I cannot figure out why.I really need some help on this.
Thank you.

---

### Post by DaV|d on 2008-03-27
lets see the interfaces again.. 
```
sudo ifconfig -a
```

Also forgot this part last time, but you'll have to set up a static ip on the windows computer too. 
example setup for the windows computer:
IP address: 192.168.0.10
Subnet Mask: 255.255.255.0
Default Gateway: <IP of ubuntu computer>
DNS server: <IP of ubuntu computer>

---

### Post by neobuddha on 2008-03-28
Here is the results:
eth0      Link encap:Ethernet  HWaddr 00:40:CA:B1:A0:4C  
          inet6 addr: 2002:4184:768b:4:240:caff:feb1:a04c/64 Scope:Global
          inet6 addr: fec0::4:240:caff:feb1:a04c/64 Scope:Site
          inet6 addr: fe80::240:caff:feb1:a04c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:534197 (521.6 KiB)  TX bytes:749094 (731.5 KiB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53700 (52.4 KiB)  TX bytes:53700 (52.4 KiB)

I don't know how to set a static ip on windows.



Do you have any idea why ubuntu won't connect to the internet anymore?The ppp error code is 2.Thank you.

---

### Post by DaV|d on 2008-03-28
Looks like eth0 is not configured for IPv4. And error code 2 indicates a misconfiguration somewhere in the ppp connection.

Lets correct that. Make a backup of your current interfaces file:
```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```

Then re-create the interfaces file:
```
gksu gedit /etc/network/interfaces
```

And copy and paste the following into the new file:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```
Save, close and reboot.

Run the following and create a new dial up connection:
```
sudo pppconfig
```
Note: to choose between options, use the arrow keys; to select an option use the spacebar; to change between the configuration options and OK or Cancel use the Tab key. Also, read carefully every screen before choosing an option.
Choose "Create a connection" and in the 3rd screen, choose Dynamic DNS.
And follow the instructions.

Finally, re-run the firestarter wizard:
Applications > Internet > firestarter 
Go to "Firewall" and select "Run Wizard"

Now for the xp computer. 
1) Go to the Start menu > Control Panel. 
2) In the address bar type "Network Connections" (without quotes) & press Enter. There you should have an icon for your lan connection. 
3) Right click on the icon > Properties. 
4) Double click on "Internet Protocol (TCP/IP)".
5) In the new window, click on "Use the following IP address:"
Fill in the following fields:
IP Address: 192.168.0.10
Subnet Mask: 255.255.255.0
Default gateway: 192.168.0.1
Preferred DNS server: 192.168.0.1
6) Click OK in both windows.
Close everything and reboot.

Please keep us posted of your progress, and good luck :)

---

### Post by neobuddha on 2008-04-03
> **DaV|d said:**
> Looks like eth0 is not configured for IPv4. And error code 2 indicates a misconfiguration somewhere in the ppp connection.

Lets correct that. Make a backup of your current interfaces file:
```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```

Then re-create the interfaces file:
```
gksu gedit /etc/network/interfaces
```

And copy and paste the following into the new file:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```
Save, close and reboot.

Run the following and create a new dial up connection:
```
sudo pppconfig
```
Note: to choose between options, use the arrow keys; to select an option use the spacebar; to change between the configuration options and OK or Cancel use the Tab key. Also, read carefully every screen before choosing an option.
Choose "Create a connection" and in the 3rd screen, choose Dynamic DNS.
And follow the instructions.

Finally, re-run the firestarter wizard:
Applications > Internet > firestarter 
Go to "Firewall" and select "Run Wizard"

Now for the xp computer. 
1) Go to the Start menu > Control Panel. 
2) In the address bar type "Network Connections" (without quotes) & press Enter. There you should have an icon for your lan connection. 
3) Right click on the icon > Properties. 
4) Double click on "Internet Protocol (TCP/IP)".
5) In the new window, click on "Use the following IP address:"
Fill in the following fields:
IP Address: 192.168.0.10
Subnet Mask: 255.255.255.0
Default gateway: 192.168.0.1
Preferred DNS server: 192.168.0.1
6) Click OK in both windows.
Close everything and reboot.

Please keep us posted of your progress, and good luck :)






It worked.Everything is working very well now.Thank you very much for your help.

---

