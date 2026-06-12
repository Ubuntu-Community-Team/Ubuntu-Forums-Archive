---
title: "How to disable wireless device or remove from startup"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rasha on 2007-05-05
Greeting.
I have MSI PC54G3 wireless PCI card , which make me lot's of trouble.
When is unplugged, everything working fine... when is plugged, Ubuntu randomly freees, i got "soft lockup detected on cpu#0", etc...
anyway.. i DON'T want to use it at all, but i don't want to remove from computer case, because I'm using in in Windows (dual boot machine)
Is there anyway to completely disable device, so ubuntu can't see it, or disable it from automatic startup.
I was edited /etc/inetwork/interfaces
and put # mark in front of every line where is wlan mentioned, but damn thing is still on.
please help, i cant find anything related in forums...


> 
 54.325858] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
 54.325864] RT61: Vendor = 0x1814, Product = 0x0302


---

### Post by starcraft.man on 2007-05-05
> **rasha said:**
> Greeting.
I have MSI PC54G3 wireless PCI card , which make me lot's of trouble.
When is unplugged, everything working fine... when is plugged, Ubuntu randomly freees, i got "soft lockup detected on cpu#0", etc...
anyway.. i DON'T want to use it at all, but i don't want to remove from computer case, because I'm using in in Windows (dual boot machine)
Is there anyway to completely disable device, so ubuntu can't see it, or disable it from automatic startup.
I was edited /etc/inetwork/interfaces
and put # mark in front of every line where is wlan mentioned, but damn thing is still on.
please help, i cant find anything related in forums...

If you have Feisty, I think you can just right click on the network manager and turn off wireless connectivity. Click "enable Wireless" so its not check marked.

Should do it :)

---

### Post by Bachstelze on 2007-05-05
If it's a module issue, disabling the connection won't solve it. To unload the module :

```
sudo modprobe -r rt61
```

---

### Post by rasha on 2007-05-05
> If you have Feisty, I think you can just right click on the network manager and turn off wireless connectivity. Click "enable Wireless" so its not check marked.

Should do it 

Thanks for quick reply, I'm having Feisty (7.04)
Yes.. it does thing... it disables it, and afterward everything works fine,  but sometimes, it can't even logon.... ubuntu freezes right after  logon screen.
So if i can automatic disable wireless it will be fine :)

---

### Post by rasha on 2007-05-05
> sudo modprobe -r rt61

That's all? It will never load again?
THANK'S A LOT...
I'm planning to buy external wireless router, and it will be final solution... until then, i don't wanna use wireless at all..
Thanks again....

---

### Post by Bachstelze on 2007-05-05
It will load when you reboot. If you don't want it to load automaticaly at boot, just edit /etc/modprobe.d/blacklist accordingly (you will still be able to load it manually if you wish).

---

### Post by rasha on 2007-05-05
> It will load when you reboot. If you don't want it to load automaticaly at boot, just edit /etc/modprobe.d/blacklist accordingly (you will still be able to load it manually if you wish).

So i just need to enter "blacklist rt61" as separate line in blacklist file?

Sorry for asking detailed explanation, I'm still newbie :S

---

### Post by Bachstelze on 2007-05-05
Yep, then just save the file and it will not load at bootup.

---

### Post by rasha on 2007-05-05
Thans again

---

