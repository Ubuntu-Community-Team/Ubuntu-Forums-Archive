---
title: "Wireless Internet."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Dave49 on 2008-02-28
I have installed Ubuntu and am experimenting with it. One major annoyance is that I have to re-enter the Hex password for my Belkin wireless router every time I reboot. Is there a way to get this thing to remember this password and log on for me?

Thanks,

~Dave

---

### Post by hyper_ch on 2008-02-28
is it WEP?

---

### Post by Dave49 on 2008-02-28
Well thanks very much. But assume I don't know what that means. I am really an "Absolute Beginner". Could you give me more detail?

Thanks,

~Dave

---

### Post by hyper_ch on 2008-02-28
[http://www.google.ch/search?q=wep&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a](http://www.google.ch/search?q=wep&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a)

---

### Post by Dave49 on 2008-02-28
I guess it's WEP. I have to enter a 30 digit hex code password.

~Dave

---

### Post by hyper_ch on 2008-02-28
if it is wep, you could hard-code it into your network config file...  but it should actually be remembered by the system... you may want to have a look at wifi-radar (although I'm not sure anymore if that handles different wifi connections - it's been a long time since I used a gui to configure my network)

---

### Post by Dave49 on 2008-02-28
It was remembered and it logged in automatically one time. Every other time I've rebooted, it asks for  the password again.

~Dave

---

### Post by hyper_ch on 2008-02-28
this is strange... it shouldn't happen...

as said, try wifi-radar... well search synaptic for it and read what it does... maybe search synaptic for other tools... I'm sure there is something in there that can help.

---

### Post by Dave49 on 2008-02-28
Thanks. I will try to figure out this Wifi Radar. I haven't quite figured out how to install programs in Linux yet. I've been using Windows for so long, it's got me spoiled with it's auto-installers.

~Dave

---

### Post by zabien1970 on 2008-02-28
Synaptic will install programs for you
System>Administration>Synaptic Package Manager
Then you can look at whats available and clicking on a package will give a brief description

---

### Post by hyper_ch on 2008-02-28
also enable the few additional repositories you have available in synaptic.

---

### Post by igknighted on 2008-02-28
You need to set-up a keyring to store the data with NetworkManager (it's much better than wifiradar most of the time, and this from a long-time wifiradar user).  Then, search the forum for a thread about storing the keyring password so you don't have to enter it every time.

---

### Post by Dave49 on 2008-02-28
> **zabien1970 said:**
> Synaptic will install programs for you
System>Administration>Synaptic Package Manager
Then you can look at whats available and clicking on a package will give a brief description

Then, if it's not listed in Synaptic it's not available for my computer? I'd like to install an antivirus program as well. I have tried Avast for Linux, and it goes through the download and install process, but then there's some errors which prevent it from being fully installed.

~Dave

---

### Post by jan quark on 2008-02-28
perhaps you have to enable the software sources

go to
system > administration > software sources 
and enable everything except source code and cd

then run in terminal

```
sudo apt-get update 
```
and try to install one more time


concerning the anti virus application
you really do not need one

---

### Post by Dave49 on 2008-03-01
BTW, the HEX password is shown in the Keyring. I have discovered that when Ubuntu asks for the Passphrase when trying to connect, I can cancel this. Then I get the double monitor with red X in the upper bar. So I click on this and tick the Belkin option (which shows good strength) and tap enter, it searches again and once again goes to the double monitor red X icon. But if I do this once more, it connects and shows the signal bars. Strange behaviour, but it's much faster than having to re-enter the 30 character HEX phrase everythime I reboot. 

~Dave

---

