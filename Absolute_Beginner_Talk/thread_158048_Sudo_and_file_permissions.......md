---
title: "Sudo and file permissions......"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-04-10
I'm really sorry if this is such a basic question but i ran a search about it on the forums and couldn't find any relevant posts......

I'm trying to fix my wireless card andive found a HowTo that seems to be relevent 
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500]("https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo#head-87c139b25904c6369b81e6640a2a6d30bf3bbeb4")
Anyway, I'm trying to modify my interfaces doc but it won't let me change the modifications that i've done. I've tried changing the file permissions but the area's "grayed out" and i cant change it. Also there's only one account (mine) installed on Ubuntu so I can't understand y it won't let me change everything. 

P.S could someone just clarify that Applications>Accessories>Terminal is the command line. or am i doing that wrong aswell?!

THANKYOU!!!

---

### Post by Darkriser on 2006-04-10
yup, that's command line (console);) .

i successfully set-up ralink drivers for my wireless adapter following this guide:
[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

Note: this is guide for setting up USB wireless adatper (rt2570 drivers). if you have PCI adapter, you should use rt2500 driver. but the process of setting up shouldn't differ much.

---

### Post by xenmax on 2006-04-10
Yes, Applications->Accessiories->terminal is one of ways to get to command line.

From terminal, type ```
gksudo nautilus 
```to change permissions, but i would suggest to use **sudo** command to edit the file in the first place rather than change permissions, especially if file is NOT in your HOME folder

---

### Post by Darkriser on 2006-04-10
as for /etc/network/interfaces file, don't change the permissions!!!
just edit it using 'sudo gedit /etc/network/interfaces' command in console.

this command (sudo) gives you temporary 'full-access' to the file. be prepared, sudo will ask you for YOUR password (just to confirm).

---

### Post by tartarian on 2006-04-10
Yes, im trying t set up the RT2500 chip. But thats my problem. The file that i need to change won't let me edit it, or change its file permissions. Any ideas?
Thankyou so much
I'm so new it scares me;)

---

### Post by Darkriser on 2006-04-10
[QUOTE=tartarian]Yes, im trying t set up the RT2500 chip. But thats my problem. The file that i need to change won't let me edit it, or change its file permissions. Any ideas?
Thankyou so much
I'm so new it scares me;)[/QUOTE]

read my post above:D

---

### Post by tartarian on 2006-04-10
Yay, thanks guys! I've managed to change the file. 
Unfortunatley that hasnt solved my overall problem, but I'm on my way. 
If any of you have any advice where I might be going wrong then please tell. I'll be able to use Ubuntu properly once i connect the goddamn thing to the world wide web!

---

### Post by tartarian on 2006-04-10
Oh My God! If its not one permission problem its another. after progressing a little bit.....

I ran this in the terminal like it told me to on the HowTo:
sudo ifconfig ra0 up
sudo ifdown ra0 && ifup ra0

and it came back with this:

ifup: failed to open statefile /var/run/network/ifstate: Permission denied

PERMISSION DENIED! How can I be getting a permission denied error when I'M IN SUDO! Im so stressed ](*,)

Help Please.

---

### Post by Darkriser on 2006-04-11
1) boot
2) open console and write:
'sudo ifdown ra0'
enter
'sudo ifup ra0'
enter
could you post here the output?

btw. isn't this progressing (little step by little step) challenging? I love it. And once you happen to solve your problem....that feeling is indescribable\\:D/

---

### Post by tartarian on 2006-04-11
At this moment im time I's finding these problems irritating. But yes, it does feel great when these little steps are overcome, and I can't wait when I actually solve the problem!

Anyway heres the output : 

oliver@ubuntu:~$ sudo ifdown ra0
ifdown: interface ra0 not configured
oliver@ubuntu:~$ sudo ifup ra0
Interface doesn't accept private ioctl...
set (8BE2) : Invalid argument
Failed to bring up ra0


I dont know what this means but it doesnt seem to be good :(

---

### Post by Darkriser on 2006-04-11
ok, could you give me content of your /etc/network/interfaces file ?
(in console use 'cat /etc/network/interfaces')

---

### Post by tartarian on 2006-04-11
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "WANADOO-3EB4"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPA
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPA="963241B24DAF56AD0966AB5B38"
        pre-up ifconfig ra0 up
auto ra0

Hope this helps

---

### Post by Darkriser on 2006-04-11
funny, coz i'm currently trying to solve the same problem...using WPA encryption on my wireless usb stick:rolleyes:

ok, error 'Interface doesn't accept private ioctl...' means, there was an error running commands 'ivpriv' in your config file. are you sure your adapter supports wpa? are you using your own home wifi router? if so, could you pls try to set only WEP encryption and then changing the interfaces file to following:

iface ra0 inet dhcp
wireless-essid <your essid>
wireless-key <your_wep_key>
auto ra0

---

### Post by tartarian on 2006-04-11
Ok, so my interfaces file now reads this : 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
iface lo inet loopback

iface ra0 inet dhcp
wireless-essid WANADOO-3EB4
wireless-key 962341B24DAF56AD0966AB5B38
auto ra0

The problem now is that it is connected and sending data, but it is not recieving any. Also thie signal strength is 0%

I'm not using my own home router i dont think. It is the one that we recieved when we signed up to Wanadoo Wireless -a livebox

Thankyou so much for helping me 
:)

---

