---
title: "Network Manager does not offer WPA"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Winterkind on 2007-01-05
Hi there!

I installed Ubuntu 6.10 yesterday and *almost* managed to get a wireless connection ;) 

Here's what I did so far:
[LIST]
[*]I installed the package network-manager-gnome.
[*]I installed the drivers for my D-Link DWL-122 USB stick (which I'm fairly proud of...).
[/LIST]
The result is that I do have the applet for the Network Manager and it even shows my WLAN. I can also select the WLAN for logon. My problem is that the logon window only offers WEP encryption but no WPA one. So I cannot logon to the WLAN...

What am I missing? I read through a few how-to guides but none really seemed to match...

Thanks in advance!

---

### Post by macogw on 2007-01-05
sudo aptitude install -y wpagui wpasupplicant

---

### Post by Winterkind on 2007-01-06
Sorry for probably being hopeless - but that has not fixed it yet.

The wpa_supplicant was already installed so I added the wpagui:
[ATTACH]22392[/ATTACH]

Nothing changed. I guess I still have to do something but I'm somewhat lost. I tried to start the wpagui but did not find it in any menu and could not start it via the terminal, either.

Here's my current situation:
The WLAN is detected correctly but when I try to logon, I get only support for the three WEP encryptions:
WEP 128-bit Passphrase
WEP 64/128-bit Hex
WEP 64/128-bit ASCII

[ATTACH]22394[/ATTACH]

Any hints?

Thanks again!

---

### Post by macogw on 2007-01-06
did you ctrl alt backspace after installing wpa stuff?  i had issues doing it too, and it turned out it was freaking out because i didnt log out and log back in.

Are you able to left click the network manager applet in the top right and tell it "connect to other wireless network"?  Is WPA an option in there?

---

### Post by petermck on 2007-01-06
I got WPA working as descibed above, but to tell you the truth, I found it quite unreliable. I probably had something wrongly configured. I'd like to gind out what it was because I prefer WPA. However, WEP is bullet proof...

---

### Post by macogw on 2007-01-06
> **petermck said:**
> I got WPA working as descibed above, but to tell you the truth, I found it quite unreliable. I probably had something wrongly configured. I'd like to gind out what it was because I prefer WPA. However, WEP is bullet proof...

Cuts out even on a strong signal, or it shows a weak signal?  Check your router's not under a desk or something and if your walls have a lot of metal that can mess with the signal (my phone doesn't work inside my house).

---

### Post by Winterkind on 2007-01-06
Hello mcogw,

yes, I restarted the X server, even rebootet. Still nothing.

Yes, I also have that option to connect to another wireless network. Same three WEP options, no sign of WPA :( 

Is there anything I should do with the WPA supplicant or the WPA GUI?

Thanks!

---

### Post by Winterkind on 2007-01-07
While reading through the WPA how-to guide ([https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)) I came across an instruction to execute "sudo iwconfig" to check if my wireless device is working. This is the output:

> lo:        no wireless extensions.

eth0:      no wireless extensions.

sit0:      no wireless extensions.

wlan0:     no wireless extensions.

Doesn't look so good to me. Unfortunately the guide does not give any instructions in such a case. Any hints?

I am quite puzzled, though, that the Network Manager is still able to find the WLAN (see my earlier post in this thread).

Thanks!

---

### Post by Winterkind on 2007-01-08
In the meantime I also tried to reinstall the network manager. No effect.

I'm sure I'm missing some important part of the configurations. Any ideas where else to check?

Thanks again!

---

### Post by spockrock on 2007-01-08
I have no idea what to tell you have you looked router side, because, I have setup wireless networks on two ubuntu machines, to use wpa with network-manager-gnome.  One uses ndiswrapper to load the drivers the other is automagically detected.  Both run fine and connect easily.....and all I did was sudo apt-get install network-manager-gnome and then restarted x and bingo it works like a charm.

---

### Post by oyvindaa on 2007-01-08
I'm not sure whether it'll help your case, but have you tried wifi-radar?

---

### Post by Winterkind on 2007-01-08
No, I have not tried that. Will do! Is there any configuration to do or is it just "install and restart"...?

---

### Post by oyvindaa on 2007-01-08
> **Winterkind said:**
> No, I have not tried that. Will do! Is there any configuration to do or is it just "install and restart"...?

You'll have to configure it (essid etc), but I can't remember if you have to restart..

It'll pop up in the Internet section of your menu.

---

### Post by mahy on 2007-01-08
What sort of wifi adapter you use? Are you sure it supports WPA? How about trying it via command line first to see if it works? (i can give you hints)

---

### Post by Winterkind on 2007-01-08
> **mahy said:**
> What sort of wifi adapter you use? Are you sure it supports WPA? How about trying it via command line first to see if it works? (i can give you hints)

My receiver is a USB stick: D-Link DWL 122. It seems to be running ok - at least the Network Manager finds my network. I installed the drivers as described in the community hardware guide for that stick.

My router is a "Fritz Box". Yes, I am sure that it supports WPA. My network is set-up as WPA and it works fine under Windows XP.

I would be very grateful if you steered me through some testing on the command line! Thanks for your help!

Any idea about that iwconfig output (earlier in this thread)?

---

### Post by Winterkind on 2007-01-17
I finally found out what is wrong: The prism2 USB driver does not support WPA!
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

Looks like I will have to use ndiswrapper. Wish me luck...

Thanks a lot for all the support so far. I might come back for more! ;)

---

