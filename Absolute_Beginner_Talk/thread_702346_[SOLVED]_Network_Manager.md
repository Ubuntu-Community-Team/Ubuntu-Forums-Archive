---
title: "[SOLVED] Network Manager"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Phil Binner on 2008-02-20
:confused:I have been struggling to connect to an Orange Livebox wirelessly. I can now get the internet by connecting with a wire, but this is a temporary solution as the computer needs to be moved. Before I made the  wired cvonnection my wireless network card seemed to be responding OK, but when I went to the network manager icon all I got was Manual network setup. The documentation describes a lot more in network management options.

Please help somebody.

---

### Post by billgoldberg on 2008-02-20
Go to "system -> administration -> network" and pick your wireless connection there.

---

### Post by Phil Binner on 2008-02-22
Whether I go into System->Administration->Network or click the Network Manager icon in the notification area (which offers only Manual network configuration), I get the same result. The network settings window opens. This allows me to select wired, wireless or medem connection, and enter details for each. There is no method of scanning for available networks and attempting connection, and no indication of whether a connection is active, in fact no dialogue at all. I have found sections in the documentation which describe a more GUI connection method than I have, but they don't seem to be activve in my system.

Meanwhile, although my wlan0 device seems to be able to see the network, I cant ping other computers or connect to the internet.

Help

---

### Post by mjwhitfield on 2008-02-22
The Orange Livebox requires that, when a new network card attaches to it, you need to press a button on the livebox to allow the MAC code. I think it's button "1", and it makes a red light flash on the box.

It doesn't work half the time, from Windows or Linux.

Anyway, if you missed that step, that would be why you can't connect

---

### Post by Phil Binner on 2008-02-22
I do have an Orange livebox, and somewhere down the line that may be the problem, but in order to know whether or not that is the case I need to get network manager doing what other people say it should, i.e scanning for networks and indulging in dialogue. I have pressed the button 1 on the livebox several times during the supposed connection process, so that should not be the problem by itself.

I have been pointed to the website [http://www.debianadmin.com/enable-wpa-wireless-access-point-in%20ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in%20ubuntu-linux.html) , which provides instructions as to how to update my network manager and shows screenshots of what it should look like. When I enter the command 
sudo apt-get install network-manager-gnome network-manager , 
I am told that my network manager is the most recent version. I also get an an error 
E: Couldn't find package network
I am connected via a wired connection during this operation
I seem to be stuck here, and I've got the feeling that the reason is that there is a concept I'm not familiar with.
So please continue to help.

Thanks - Phil B

---

### Post by alan34 on 2008-02-22
To scan for wireless networks in a terminal go (assuming wlan0 is your wireless interface)
(more /etc/network/interfaces)

sudo iwlist wlan0 scan

Should list the networks near to you

but if you know your network name (ESSID), type of encryption and DNS server IP address
just enter them in Network Manager through the manual configuration.

Good luck

---

### Post by Phil Binner on 2008-02-22
The scan in terminal has found my livebox, which is the strongest signal, but strangely has not noticed any of the other signals which are about.

Thanks to Alan34, but I entered the ESSID, encription and DNS information on my first attempt (about n zillion attempts ago), and also put the livebox in pairing mode, but no joy.

I can't help feeling that one thing I have not actually done is to tell ubunto to try to connect. There seems to be an assumption that it will do this on it's own, but will it. Also, the graphics I have seen displayed elsewhere seem to permit a network to be selected and connected. This is also described on the Ubunto website. Why do I not get this option and is it something to do with my problem.

Thanks

Phil B

---

### Post by alan34 on 2008-02-22
You could try editing the text file that sets up the wireless network.

gksudo gedit /etc/network/interfaces

Do not delete any lines


iface wlan0 inet dhcp
wireless-key YOURHEXKEY                (sorry mine is WEP so can not tell you WPA)
wireless-essid YOURNETWORKNAME

auto wlan0

Then edit

gksudo gedit /etc/resolv.conf

nameserver 192.168.0.1               (IP address of your router - this is mine yours might be different)

Good Luck

---

### Post by Phil Binner on 2008-02-22
Thanks to all, particularly Alan34; I am now sorted. Not being at all technical I thought I had a WEP key, where it was, in fact, WPA. It took quite a few goes to get everything right because the changes I put into the setup properties box were not reflected in the file. In particular, my 26 char key didn't go in at all correctly, and an earlier attempt to set the ip address manually didn't get removed when I went back to DHCP. Being able to see and correct the file told me what was happenning, and it's now OK.

I am still confused as to why I don't have the GUI facilities I have seen on other peoples screen shots, and seem to be described in the documentation, and if anyone can enlighten me I'd be delighted.

Alan, my email is phil.binner@gmail,com. I'd appreciate a chat if you're willing.

Thanks again. Phil B

---

