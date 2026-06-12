---
title: "YAY! I got ubuntu loaded finally - now for wireless internet [MerryXmas, Happy Newyr]"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-12-26
OK. so i salvaged my old computer and pretty much took out everything but the floppy drive, mobo and proc. I got the old DVD drive out, and it worked! So I immediately wiped XP and put ubuntu...

This is a secondary computer, about 6 years old with a PIII 1gz and 512mb of ram.

Before I do any wierd stuff:
I used the alternate install CD, worked like a charm and have 7.10 ubuntu

I am trying to get wireless to work from my ACTIONTEC router.

the pass key is "   WEP 64-bit:"

when i go to input it , i get options of 64/128bit HEX, something about ASCI (or something like that) and regular WEP 128bit keys. Which do I choose? I tried all of them and none take my code :(

Please help, 
Future ubuntu user

---

### Post by icheyne on 2007-12-26
Convert your WEP password into hex and choose the 64/128 HEX option. Here is a description of the process:

[http://blogs.ittoolbox.com/wireless/networks/archives/converting-a-phrase-to-hex-for-a-wep-key-13024](http://blogs.ittoolbox.com/wireless/networks/archives/converting-a-phrase-to-hex-for-a-wep-key-13024)

Incidentally WEP is totally broken. If your router and wireless card support it, use WPA instead.

---

### Post by Hospadar on 2007-12-26
is your key made up of characters 0-9 a-f (or A-F)?  if that's the case you want 64 bit hex  if there are alphabetic characters other than a-f you want ascii.
The problem however may not be the setup. but rather your wireless card if it isn't supported well by ubuntu.

Also too, I've often had better luck manually configuring the wireless as opposed to letting network manager do it.  network manager periodically scans for networks on wireless cards and this can cause some cards to drop connections.  Especially if you are using wep encryption (not WPA) it's easy to configre your wireless connection in the /etc/network/interfaces

For example, here's my /etc/network/interfaces file ```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid MY_NETWORK_NAME
        pre-up iwconfig wlan0 key 746b9efadd5b0c9b5f46429347

```A bit of explanation, "lo" is the loopback interface, for localhost connections, eth0 is my wired connection, it's commented out with '#' because I'm not using it right now.  in the wlan0 section, there is the essid (the name of your wireless network) and your key (if you are using a 64 bit key this will be much shorter).  also note that the "auto" in "auto wlan0" line means that that interface comes up automatically on boot.

Once you have your connection set up in the file, you can either restart or do a "sudo ifup wlan0"

=====
In other news:
If you arn't sure your hardware is working with linux at all, try going to a terminal and typing "iwconfig" this will list all your detected network adapters and whether or not they are wireless capable.

If you go the route of manual configuration, you may want to read up some more on the /etc/network/interfaces file and see if there are other things you need/want ALSO:  If you go that route, you'll want to purge network manager and network-manager-gnome from your system and reboot before you do any of this, because if network manager is causing the problem, it will continue causing problems. also if you installed wifi-radar purge it as well ```
 sudo apt-get --purge remove network-manager network-manager-gnome wifi-radar
```Also, since getting rid of these will cause you not not have that little icon in the corner for networks, and your wired networks will not come on either unless you manually configure them in your interfaces file, you may want to re-install network-manager and network-manager-gnome before you purge them, this will cause their package files to remain in the package cache, so you can re-install them without a net connection ```
sudo apt-get --reinstall network-manager network-manager-gnome
``` (Also note I think these are found on the CD so you can probably get them there as well)

Hope this gives you a little direction if it doesn't solve your problem!  Indeed this may be a lot of bother over a minor misunderstanding of passwords, but it might help

---

### Post by Chayak on 2007-12-26
Dito on WEP being worthless.  On a bad day while multitasking it takes about five minutes to crack it and own your router.  Use WPA/WPA2 with a strong passphrase.  It's pretty much useless if you use something that's in a dictionary file somewhere.  Use a passphrase with numbers, caps, and special characters.

---

