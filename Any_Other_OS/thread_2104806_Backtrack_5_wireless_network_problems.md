---
title: "Backtrack 5 wireless network problems?"
date: 2013-01-14
forum: Any Other OS
---

### Post by berry1 on 2013-01-14
Having a slight problem with my wireless network! I installed Ubuntu 12.10 on my windows 7 laptop but decided i wanted to go with backtrack 5 r3 instead after sampling it from usb. So i installed Backtrack 5 last night and everything was working well including my wireless network connection.   When i booted up today and opened Wicd no wireless connections where detected only my wired connection was available to connect to. So i tried a number of different commands to start networking ect but nothing will work. Then i booted Ubuntu 12.10 from my usb again and also could not connect to my wireless connection on Ubuntu.   When opening Wicd > Preferences then under network interfaces the wireless interface box is empty and the wired interface has ech0.   Would really appreciate if someone could advise me on this as last night my wireless was working fine on Backtrack 5 and Ubuntu.  

        description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 02

---

### Post by berry1 on 2013-01-15
I figured that my network card was probably not compatible with backtrack so bought a netgear usb wireless adapter. Wicd shows the available wireless networks to connect to but wont connect to my network :(. 

I tried disabling encryption but it says 'this network requires encryption to be enabled'. Then i changed the encryption to WEP and got the error message 'Could not obtain IP address' then tried changing it to WPA and got a different error message 'Bad password'.  

Could someone please advise me on this?  
Thanks!

---

### Post by berry1 on 2013-01-15
Update: Wireless network connection now working with encryption disabled anyone know how i can enable my network encryption and still connect through wicd? Because right now im back on the wired connection as i don't  want to use my network unsecured.   
Thanks!

---

### Post by hecoo on 2013-02-06
i have installed backtrack 5 r2 and i install network gnome manager ,with VPN connection i'm going on internet ,that's ok ,
problem is next,  i buy new computer ,install bt and now i can not connect to VPN ,everything is ok but vpn connection is failed every time i try to connect 
when i replace HDD to old computer and start BT i can connect to VPN ,put the HDD back to new computer and again the same error ,


any help ?

---

### Post by UltimateCat on 2013-02-09
> **berry1 said:**
> I figured that my network card was probably not compatible with backtrack so bought a netgear usb wireless adapter. Wicd shows the available wireless networks to connect to but wont connect to my network :(. 

I tried disabling encryption but it says 'this network requires encryption to be enabled'. Then i changed the encryption to WEP and got the error message 'Could not obtain IP address' then tried changing it to WPA and got a different error message 'Bad password'.  

Could someone please advise me on this?  
Thanks!

Hi:

Depending on what network card you have it may just be that you need a driver. A list of cards are on this page
[http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

This Netgear works

[LIST]
[*] [COLOR=#339966]Netgear wg111v2 [/COLOR] - using the mac80211 rtl8187 drivers-[COLOR=#3366ff]passed IF this is the one you have[/COLOR]
[*][COLOR=#3366ff]Which Netgear USB Adapter do you have? The wg111? wg311v3? wpn111?
[/COLOR]
[/LIST]


To find out what network interface card you have you can open the terminal and run the command:
```
lspci

```Post the output to that command so others can read the output and help you.

---

### Post by UltimateCat on 2013-02-09
I wasn't sure if you are East Coast or West to choose the driver for you.
Scroll down to about the middle of the page and you'll see the Linux Drivers.

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?LANGID=1&PNID=13&PFID=5&LEVEL=5&CONN=4&DOWNTYPEID=3&GETDOWN=F](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?LANGID=1&PNID=13&PFID=5&LEVEL=5&CONN=4&DOWNTYPEID=3&GETDOWN=F)

In my case I had to download the driver for my USB Adaptor and a driver for my NIC and after I installed the drivers I was able to get Ubuntu online.

---

