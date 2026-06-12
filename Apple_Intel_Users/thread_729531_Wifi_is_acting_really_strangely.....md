---
title: "Wifi is acting really strangely...."
date: 2008-03-19
forum: Apple Intel Users
---

### Post by Grafdude on 2008-03-19
I have an apple mbp SR 2.2ghz with the atheros 5418 wifi chip and also have ubuntu 7.10 on it. At first when I installed the madwifi drivers from source (installed with no glitch), my internet didnt want to work afer configuring it accordingly to my router's setup. I have a router (dlink WRT54GL) that is set up with no dhcp (static ip) with wpa psk security. I used the network manager within ubuntu to set it "manually", entered the desired ip adress, subnet, gateway, wpa password and my isp's dns server adresses.

My internet never worked under those settings, anyways I installed the madwifi-ng patched drivers (to be used with aircrack-ng) since thats the whole reason why I installed ubuntu, for experimenting with network security. I was able to crack my own network with aircrack, and also some of my friends network too, but for some reason I cannot make my internet work when my router has dhcp disabled. I put dhcp on for testing, configured network manager accordingly,  and my internet worked! But it seems like ever since I installed the madwifi-ng drivers, even with dhcp, I cannot browse the internet even though I can crack wifi networks!!!

---

