---
title: "Can't connect to WPA wireless networks- 802.11b Cisco Wireless Card, IBM X31"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by pitseleh on 2007-06-22
I am currently running my very first Ubuntu Linux install on my IBM X31 laptop. Everything has been working great except I cannot connect to WPA protected wireless networks. When I try to connect it says: 

"Error connecting to wireless network. The requested wireless network requires security capabilities unsupported by your hardware."

Unfortunately, I have not been able to test it on an open wireless connection, but a dialogue box comes up when I try to connect to my neighbors WEP connection, so I'm assuming if I had their passkey, it would in fact connect.

I've looked online a ton for some sort of drivers (Aironet?) that would help me, and also have looked into terminal commands that would enable it (but the instructions were for an older version). So I'm stuck... I'm not sure what to do.

My laptop information is:
ThinkPad X31 2672-CXU 
 Cisco 802.11b wireless(MPCI)

I found this page, but I don't know what to make of it...
[http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)

Thanks in advance! Sorry I'm such a newbie.

---

### Post by shearn89 on 2007-06-25
hey - this might help:

1. Check [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for info on your card.
2. If it says something about ndiswrapper, use [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") howto.
3. Then if it still doesn't work, i'd recommend trying a different network manager, perhaps Wicd? have a search on these forums.

---

### Post by lazyart on 2007-06-25
I have a Cisco Aironet in my laptop and it doesn't support WPA either (it does in Windows, so you know what the real issue is-- lack of vendor support).

---

### Post by pitseleh on 2007-06-26
I tried ndiswrapper but unfortuntaely, my card was not on their supported list. I also tried Wicd, but it kept locking up so it's gone now.  I found this: [http://bellet.info/laptop/t40.html#wireless](http://bellet.info/laptop/t40.html#wireless) which was a project to create wireless drivers for my card that work. They're old, but I'm hoping they support WPA. I downloaded them and I have no idea what to do with them now.

lazyart, did you find a fix to get WPA supported on your Aironet card?

The Windows user in me is thinking... I've installed all this extra crap on my computer, and modified some stuff... is it going to become unstable? ;)

---

### Post by shearn89 on 2007-06-26
i'm not sure how to isntall the drivers, but your system won't become unstable - don't worry.

---

### Post by ugm6hr on 2007-06-26
> **pitseleh said:**
> I tried ndiswrapper but unfortuntaely, my card was not on their supported list. I also tried Wicd, but it kept locking up so it's gone now.  I found this: [http://bellet.info/laptop/t40.html#wireless](http://bellet.info/laptop/t40.html#wireless) which was a project to create wireless drivers for my card that work. They're old, but I'm hoping they support WPA. I downloaded them and I have no idea what to do with them now.

lazyart, did you find a fix to get WPA supported on your Aironet card?

The Windows user in me is thinking... I've installed all this extra crap on my computer, and modified some stuff... is it going to become unstable? ;)

Shame that Wicd misbehaved on your system.  I had the same error on one of my laptops with a prism2 PCMCIA wifi card when using Network Manager (worked fine with WEP).  Wicd solved the problem (with WPA-PSK TKIP).  I found that Wicd 1.2.7 was more unstable than 1.2.9 with Feisty, and requires Network Manager to be uninstalled, and the computer rebooted before it will work.

It appears that your card has a cisco chipset though, so whether this is of any value to you...

PS: you could confirm chipset with *lspci* in Terminal

---

### Post by pitseleh on 2007-06-26
I'm definitely stuck. I've learned a ton about my card, but I still do not know how to get it to even give me the option to connect to WPA networks. The link I provided in my last post did not get me anywhere. It was structured for an older version and somehow even though they were referencing my card, the Read Me was talking about PCMCIA cards.. so.

I learned that my cards PCI ID is 14b9:a504, the chipset is Cisco, and when I type in lspci it has this entry:
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

I followed the Wicd instructions, uninstalled the Network Manager and all, but it still freaked out on my machine. I'm thinking I'm going to give it another go, but I'm afraid the problem is with the Aironet driver itself.

---

### Post by jonnymccullagh on 2007-06-29
This thread really helped me thanks.
In case it might help anyone else in "How do I sort out this one?" web search land.

I am helping a friend install Ubuntu 7.04 on an E-system 3086 (Ubuntu 6.10 worked fine except for the wireless).
In Ubuntu 7.04 I could now see the wireless networks and their strengths but when trying to connect to my WPA-protected network I got an error message:
[INDENT]Error connecting to wireless network
The requested wireless network requires security capabilities unsupported by your hardware.[/INDENT]
Weird since I knew the wireless adapter (Realtek RTL8187) worked with WPA in Windows.

So after reading this thread I tried [Wicd]("http://wicd.sourceforge.net/") - I read the very short FAQ and uninstalled network-manager (using Synaptic). I then downloaded and installed the Wicd deb file.

It worked and allowed me to enter my WPA passphrase. The [FAQ]("http://wicd.sourceforge.net/wiki/doku.php?id=faq") also includes short instructions on getting the tray icon to appear.

If you are having trouble try Wicd - it'll take about 10 minutes to try and is safely reversible!

I marvel at the Gnu/Linux community every day!

---

