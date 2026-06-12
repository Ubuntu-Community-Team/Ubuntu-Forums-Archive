---
title: "No internet connectivity with Kubuntu (via ICS)"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by krhamm on 2006-08-10
I took a dive into the Linux pool two days ago by installing Kubuntu 6.06 from a Live CD. Within an hour or so my plodding Fujitsu P2040 with 700 MHz Transmeta Crusoe chip was transformed into a usuable computer from it's previous sluggish Windows existence! I am very, very impressed!

However, I have yet to be able to get internet access either at home (ADSL) or at work (Ethernet). In both cases I am sucessfully connecting to Windows XP machines using Internet Connection Sharing (ICS). In both cases I can see and access shared Windows drives. However, no internet (yet)!

I'm trying to figure out the correct settings in **System Settings** > **Network Settings**. At work the ICS machine has two network cards, one connecting it to the ISP, and the other to the network hub. The ISP card uses a DNS of 10.91.0.1 and a subnet mask of 255.255.0.0. The LAN card uses a DNS of 192.168.99.1 and a subnet mask of 255.255.255.0.

Under the **Network Interfaces** tab I've got an IP address (automatically assigned) of 192.168.99.7 with a netmask of 255.255.255.0 using DHCP protocol. To my understanding, it looks perfectly fine. On the **Routes** tab I wasn't sure what IP address to enter. I've put in 10.91.0.1 since that's what the WinXP machine has.

The real mystery to me is what should be entered under the **Domain Name System** tab. I've tried a number of things and nothing seems to make a positive difference.

Hopefully someone can steer me in the right direction so I can move on to solving other mysteries! :p

---

