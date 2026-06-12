---
title: "Kubuntu can't pick dynamic LAN connections"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by sister_clamp on 2006-09-23
Hi everyone--

This is more an annoyance than a show-stopper but a frequent one for me. I have installed Kubuntu 6.06 (love it!!) and find that, if I've started a session offline, then plug in my RJ45, Kubuntu does not dynamically detect the LAN connection. In order to, say, connect to the internet via my router, I have to reboot the machine. Even just restarting the session (Ctrl+Alt+Bkspace) doesn't work; it has to be a full shutdown, then restart with the RJ45 inserted when the kernel is booting. 

Is there any way around this? (Damn but this is one irritation that, unfortunately, Windows handles better!)

Sincerely,
S_C

---

### Post by Indras on 2006-09-23
Networking connections are set up before your graphical interface starts, so by using CTRL+ALT+Backspace to restart the x server won't affect the networking at all.

You can use the command: ```
sudo /etc/init.d/networking restart
```Or you could go to System->Administration->Networking, select your ethernet card, then disable and re-enable.

---

### Post by crokett on 2006-09-23
You can also try the ifdown and ifup commands on your interface.  

```
sudo ifdown <yourinterfacehere>  
      sudo ifup <yourinterfacehere> 
```

System->Administration->Ethernet will show you what interfaces you have (eth0, eth1, etc)

---

### Post by sister_clamp on 2006-09-24
Great! Thanks guys! Think I'll go with the sudo command as that seems the most elegant. Will try the next time I move from off- to on-line.

S_C

---

### Post by yhurtock on 2007-02-21
hey man i need help, i want to share internet connection with a winxp pc from my kubuntu, but i just did it by asigning a static ip on client computer, i want it to be dinamic, i have firestarter installed too, ill really apreciate any help thank u.

---

