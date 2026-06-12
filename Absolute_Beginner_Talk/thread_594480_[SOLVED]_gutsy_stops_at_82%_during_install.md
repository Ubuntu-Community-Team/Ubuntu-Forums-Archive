---
title: "[SOLVED] gutsy stops at 82% during install"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-10-28
Tried to install gutsy onto a new slave drive. It stops at 82% during the install when it says it is checking ubuntu.com for updates. The install does not progress from there and then I am left with a mucked up grub that stops me booting into my master drive which has xp and feisty.  (I have found out how to fix this). 
Anyone know a work around or fix for the install stopping at 82%? I have checked the md5checksum of the iso file and it is fine.

---

### Post by Qwerty_ on 2007-10-28
Just disconnect your Internet.

---

### Post by bumanie on 2007-10-28
Thanks for the suggestion qwerty. I just got to work so won't have achance to try that for 18 hours or so, but it's certainly a good suggestion. Will post a solved if it works.

---

### Post by skymera on 2007-10-28
mine stopped at 82%....i left it and shortly after it zoomed up :S

try above and just leave it :)

---

### Post by jenhsun on 2007-10-28
Basically when you enable your network from the beginning, it will try to link to the internet and have a search or something. I just wait for this task done.
You can try to disable at the beginning. It might help.

---

### Post by bumanie on 2007-10-28
> **skymera said:**
> mine stopped at 82%....i left it and shortly after it zoomed up :S

try above and just leave it :)

Thanks for the advice. The first time I tried it sat for at least an hour and finally came up with a message that it couldn't connect to ubuntu.com. I clicked OK and the install continued, however it stuffed up the bootloader (which I have now fixed). Problem was I could not access the slave drive to see if anything useable had installed. The second and third time I tried to install gutsy, it stopped at 82%. After three failed attempts and having difficulty getting my computer going at all (ie receiving both grub error 17 and 22 at different times), I have been reticent to retry another install. Have not tried again since resurrecting grub. May be now I know (thanks to this forum) how to restore grub, I can try again. 
Is there anything special I should do to get a successful slave install with gutsy and have it successfully boot with the master drive which has xp and feisty on it?

---

### Post by bumanie on 2007-10-30
Finally got gutsy installed. It hung at 82% for about 20 minutes then the install finished. However, I now have problems with booting and internet connection. Will make a new thread about these issues.

---

### Post by jenhsun on 2007-10-30
> **bumanie said:**
> Finally got gutsy installed. It hung at 82% for about 20 minutes then the install finished. However, I now have problems with booting and internet connection. Will make a new thread about these issues.

Not necessary, Search this forum first.
If you still can solve it by yourself, post your problem in detail.

---

### Post by bumanie on 2007-10-30
> **jenhsun said:**
> Not necessary, Search this forum first.
If you still can solve it by yourself, post your problem in detail.

I have not been able to find anything that helps on the forum. I did look first. I have made a new thread posted 1 hour + ago. No suggestions from anyone so far.

---

### Post by jenhsun on 2007-10-30
> **bumanie said:**
> I have not been able to find anything that helps on the forum. I did look first. I have made a new thread posted 1 hour + ago. No suggestions from anyone so far.

Sorry for not response to the other thread. let's step by step.

[Internet connection]

1. Go to your System/preference/Hardware Information
and try to find out your network card info. is that eth0 or eth1?
Make sure your system already know your network card.

2. If your computer automatic receive ip from your router, which mean you have dhcp
If don't, that means you use static ip service.
Go to your terminal and 

sudo gedit /etc/network/interfaces
You will see similar like this
#For Your DHCP
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

#For your static ip
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.0.18
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
```


And post what you get after your setting.

---

### Post by bumanie on 2007-10-30
> **jenhsun said:**
> Sorry for not response to the other thread. let's step by step.

[Internet connection]

1. Go to your System/preference/Hardware Information
and try to find out your network card info. is that eth0 or eth1?
Make sure your system already know your network card.

2. If your computer automatic receive ip from your router, which mean you have dhcp
If don't, that means you use static ip service.
Go to your terminal and 

sudo gedit /etc/network/interfaces
You will see similar like this
#For Your DHCP
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

#For your static ip
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.0.18
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
```


And post what you get after your setting.

Sorry I can't try anything right now as I am work. What I can say is that in feisty I had no problems and it does work via DHCP (still on master drive and working). Can you kindly have a look at this forum page 2 (towards the bottom) "Gutsy problem - no internet, grub error 17". My present problems are detailed there. May be the explanation there will give you an idea of what my problem is.

---

