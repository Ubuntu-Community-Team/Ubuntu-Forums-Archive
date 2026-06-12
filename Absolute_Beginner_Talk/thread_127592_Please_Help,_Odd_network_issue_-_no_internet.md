---
title: "Please Help, Odd network issue - no internet"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by hybridmedia on 2006-02-09
Thanks in advance for any help you can give,

installed 5.10 on 2 pcs and get the following issue
networking is configured correctly either by DHCP or static, same settings work on my mac and pc.
But I am unable to go to any website or use GAIM as OS is not resolving the IP corrrectly, If I use an IP address the webistes come up fine
I have tried the IP of the router (which usually works as the dns server and the real IP addresses of the dns server of the ISP, no change

If I go to to the network tools and use ping tracert etc it is resolving the dns correctly. This is driving my nuts  :cry:

---

### Post by rado_london on 2006-02-09
The think that I would do in that stuation is to see if the network connecttions are enabled.
Try this :
```
sudo ifup "your interface ie eth0"
```

Without the " "


Good Luck

---

### Post by hybridmedia on 2006-02-09
[QUOTE=rado_london]The think that I would do in that stuation is to see if the network connecttions are enabled.
Try this :
```
sudo ifup "your interface ie eth0"
```

Without the " "


Good Luck[/QUOTE]
When I try that it says it is configured, what I think I also failed to mention is I can access samba shares without issue, its only websites with domain names. yet the ping etc work fine...most odd

---

### Post by rado_london on 2006-02-09
Hahaa this is really odd. What browser do you use?

---

