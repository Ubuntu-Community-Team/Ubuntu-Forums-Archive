---
title: "Computer &quot;sees&quot; wireless APs but won't connect. MBP 7.1, Kubuntu 14.04. BCM4322"
date: 2014-06-03
forum: Apple Hardware Users
---

### Post by minorsecond on 2014-06-03
Hi all, 

I originally posted this to AkUbuntu but haven't really gotten any help (don't know how active it is), so I'm posting it here. Not a new user so please don't think I"m a "hit & run" guy. I don't know why my username was "reset." 

Anyway, if you'll please forgive me for the copy/paste:

[COLOR=#333333][FONT=UbuntuRegular]I desperately need some help (maybe not desperately, but this is frustrating!). I have a Macbook Pro 7.1 with a Broadcom BCM4322 wireless card. I have tried, and tried, and tried to get it working but it refuses to cooperate. I've searched here and nothing I've found works. Currently I have loaded bcmwl-kernel-source (as you will see in the pastebin link) but that doesn't work. The most interesting thing is that I got it to work with no problems on Lubuntu 14.04 using firmware-b43-installer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here's what I've tried (repeatedly):[/FONT][/COLOR]

[LIST]
[*]bcmwl-kernel-source
[*]b43-fwcutter & firmware-b43-installer
[*]linux-firmware-nonfree
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]I've tried each individually, and various combinations of the three (I know that won't work, but I thought *just maybe*).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Anyway, I ran the wireless-info script and [the output is here]("http://pastebin.com/rMjVmGvh").[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thank you so, so much for your help![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Quick specs:[/FONT][/COLOR]

[LIST]
[*]Kubuntu 14.04 (3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux)
[*]Broadcom BCM4322
[*]Even tried wicd instead of network-manager (didn't help)
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]**EDIT: reinstalled linux-firmware-nonfree and now the computer scans for wireless networks, but does not connect. Posted [new output of wireless-info]("http://pastebin.com/9yxWjL0X"). Maybe the following is important:**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][ 657.716057] wlan0: authenticate with[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][ 657.744251] wlan0: send auth to (try 1/3)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][ 657.746953] wlan0: authenticated[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][ 662.752366] wlan0: deauthenticating from by local choice (reason=3)[/FONT][/COLOR]

---

### Post by minorsecond on 2014-06-05
Interestingly enough, if I restart the computer, it no longer detects wireless networks. I have to reinstall the driver each time. But it still doesn't connect to anything, regardless of wireless security configuration. Even if I create an unsecured network, it won't connect.

---

### Post by varunendra on 2014-06-05
Welcome to the forums minorsecond!

Can you try changing the router's encryption to WPA2-PSK with AES (CCMP) please? Currently it is using WPA(1) with TKIP, and TKIP may cause performance or even authentication issues sometimes.

If the problem persists, I would like to see the report of **[this script]("http://ubuntuforums.org/showpost.php?p=13024222")** (it's a modified version of the original one, providing more info) with the STA (bcmwl-kernel-source package) driver installed instead of b43.

---

### Post by minorsecond on 2014-06-05
> **varunendra said:**
> Welcome to the forums minorsecond!

Can you try changing the router's encryption to WPA2-PSK with AES (CCMP) please? Currently it is using WPA(1) with TKIP, and TKIP may cause performance or even authentication issues sometimes.

If the problem persists, I would like to see the report of **[this script]("http://ubuntuforums.org/showpost.php?p=13024222")** (it's a modified version of the original one, providing more info) with the STA (bcmwl-kernel-source package) driver installed instead of b43.

Thanks for the reply, varunendra!

So I just removed linux-firmware-nonfree and replaced it with bcmwl-kernel-source. With the latter, it won't even detect wireless APs. The former will, but won't connect (even with WPA2/AES). I went ahead and ran that script with bcmwl-kernel-source loaded.

[wireless-info.txt]("http://pastebin.com/UdB7JdDv")

---

### Post by varunendra on 2014-06-05
It seems you are trying the drivers in the same session. Please reboot and try again with the same 'wl' driver.

Also, assuming you are in US, please do -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
..before rebooting. If you are in a different country, not US, use your country's code. To find your country's regulatory domain code, please refer to this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

If it still can't scan networks, purge the sta driver -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot. The "b43" will load again automatically (you may have to reinstall the "linux-firmware-nonfree" package. You didn't need to remove it at all..). Post back a fresh report with "b43" this time.

---

### Post by minorsecond on 2014-06-05
Confused myself with firmware versions.The firmware that does scan networks is "firmware-b43-installer." Linux-firmware-nonfree does not work.

I did all that you said, and the bcmwl-kernel-source firmware still didn't work. Reinstalled firmware-b43-installer. Then, the list of networks appeared. Tried to connect - nothing. Rebooted. The computer now won't scan for networks.

[New Wireless-Info]("http://pastebin.com/C2yy5Esh"), after reboot.

---

