---
title: "wireless problems"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by anfractuosities on 2007-04-12
I cant get my wireless to work.

intel WM3945AGM1WB Mini PCI 802.11 

help please...

it is recognized...but i want to connect to my schools's wifi...

---

### Post by compmodder26 on 2007-04-12
What version of ubuntu are you using?  It should be working out of the box.  Mine has worked out of the box since Dapper. Make sure you have the restricted modules installed for your kernel.

edit:  I must of missed your last line when reading your post.  So it is detected properly, but you just don't know how to get it to connect, right?  Again, what version are you using?  I ask because, I've always used network-manager to get my wireless going and it isn't installed by default in anything before Feisty (7.04).  I would suggest installing network-manager first.

---

### Post by Malakia on 2007-04-12
Do you have it set to DHCP or a static connection, if its set to the latter than it won't work.

---

### Post by anfractuosities on 2007-04-12
it is set to dhcp

restrited modules are installed

i am running edgy

thanks

---

### Post by compmodder26 on 2007-04-12
I've edited my last post with some more information.  Try that out.

---

### Post by dca on 2007-04-12
Are you using WiFi Radar or network-manager or CLI to scan for access points?

---

### Post by anfractuosities on 2007-04-12
network manager is installed...were do I open it from? or can I? I cannot find it in any menu.

wifi radar

---

### Post by compmodder26 on 2007-04-12
I'm assuming you are using Ubuntu and not Kubuntu, so you will also need network-manager-gnome installed also.  After it is installed, type nm-applet in a terminal.  A new icon should show up in your system tray on the gnome panel.

---

### Post by anfractuosities on 2007-04-12
That icon was already there. but it only establishes a link for my wired connection.  It is two computers right, the icon?

---

### Post by oilchangeguy on 2007-04-12
click on the icon, and from the drop down menu select wlan0.

---

### Post by anfractuosities on 2007-04-12
that is not an option, it only says "wired"

i have to leave my wired  connection for now...i'll be active on it later... thanks for all your input so far.

---

### Post by compmodder26 on 2007-04-12
Been a while since I used wired on my laptop, but if I remember correctly, network manager will default to wired if an ethernet cable is plugged in.  It will only switch wireless on if no ethernet connection is established.  Again, it's been a while, so I may be wrong.

---

### Post by anfractuosities on 2007-04-12
it still doesn't connect to wireless...it just has a grayed out wired connection

---

### Post by tux_rox on 2007-04-12
2 Questions:

1)  What's "static" and "DHCP"?

2)  Will all this mess be fixed in Feisty?

Thanks a lot!

---

### Post by anfractuosities on 2007-04-13
bizump

---

### Post by anfractuosities on 2007-04-13
i really want to love linux....

---

### Post by compmodder26 on 2007-04-13
Okay, try this.

Open /etc/network/interfaces and comment everything out except the section pertaining to the loopback interface (lo).

Try a restart and see if network manager can see use your wireless card this time.

---

### Post by anfractuosities on 2007-04-13
ALright!!!  network manager now recognizes my wireless card...but it still wont connect to a network...it tries, and i think it did once for a split second...I know the connection is strong b/c i got it in xp....

Thanks so much for all your help

this is my iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:477   Missed beacon:0

sit0      no wireless extensions.

---

### Post by compmodder26 on 2007-04-13
So, if you left click on on the network manager icon, does it give you a list of available wireless networks?

---

### Post by anfractuosities on 2007-04-13
only the one i created with "connect to other wireles network"

---

### Post by compmodder26 on 2007-04-13
Does the network you want to connect to require any encryption like WPA or WEP?

---

### Post by anfractuosities on 2007-04-13
there are 6 availbe from my school a-wpa a-wep and a-open  and the same for bg

---

### Post by compmodder26 on 2007-04-13
And you can't connect to any of them?

---

### Post by anfractuosities on 2007-04-13
correct

it is also showing networks that i did not enter now too, they all have signal but it will not connect

---

### Post by compmodder26 on 2007-04-13
In those networks that you do see, if any of them have what looks like a shield in their display, that means they are encrypted.

As for not being able to connect, I'm a little stumped now.  I've been able to connect just fine and I have the same card.  I can only suggest double checking the network information you are entering to make sure it is correct.

---

### Post by anfractuosities on 2007-04-13
some of them are encrypted, but i have the passkeys, also, once i enter the network info, how do i edit it?

---

### Post by compmodder26 on 2007-04-13
You just click on "Connect to other wireless network" or "Create new wireless network".

---

### Post by anfractuosities on 2007-04-13
OK Its WORKING, at least to the open network, thats good for now!!!


Thank You so much! I am very new to Linux, like a few days old, but I think it is a fantastic community, and I wish to give it my support...


CHEERS!

---

### Post by compmodder26 on 2007-04-13
Glad to hear that you got it sorted for the open network.  It should also work fine on the encrypted networks too (I emphasize SHOULD).

---

