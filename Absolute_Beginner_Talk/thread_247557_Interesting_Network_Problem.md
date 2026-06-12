---
title: "Interesting Network Problem"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by MrSt0ne on 2006-08-30
I have this problem, where I cannot connect to the interent when I install Ubuntu onto my box. But heres the kicker, I can get online while running off of the live CD. And when I configure the installed linux to get onto the network, and I restart, it hangs up and I have to restart my computer and reinstall linux in order to get it to work without the network, so its get really annoying fast. If anyone can help me out, it would be really really useful. ](*,) 

Also bonus points, I got a new Videocard, after I installed linux, and Its not picking it up, and when I dual boot, I cannot see the Grub unless i plug into my onboard videocard.

Thank you very much for your time, and attempts.

---

### Post by Tarvok on 2006-08-30
I can't help you with the video card problem, but how are you accessing the internet? Are you on a LAN? Dial-up? Cable or DSL modem?

---

### Post by MrSt0ne on 2006-08-30
I am trying to connect to my router via wireless which then connects to a DSL modem, in which connects to Surewest, my ISP.

---

### Post by nmaclennan on 2006-08-30
I don't know if this will help or not but I had to configure the router to LOG ON to the ISP for me. Originally with XP it did the LOG ON and passed it through the router to the modem.

I hope this helps as I am new to Ubuntu and it is a real experience for this OLD brain.

---

### Post by cwaldbieser on 2006-08-30
> **MrSt0ne said:**
> I am trying to connect to my router via wireless which then connects to a DSL modem, in which connects to Surewest, my ISP.

I am guessing that you use DHCP to connect to your router (rather than a static IP address).  I would suggest you boot into the installed version and try this command:

```

$ sudo dhclient

```
It will attempt to connect to your router via DHCP.  It will NOT save the settings or make them permanent, so if you reboot, it will not have changed anything that will freeze your computer.

One thing I wonder about-- when your computer froze, was anything displayed on the screen.  Some folks have a problem trying to get the network time and it makes Ubuntu appear to freeze (it will actually time out after a pretty long time and finish booting).  In this case, you could just disable the network time sync.

---

### Post by MrSt0ne on 2006-08-30
When it freezes on boot, it will boot like normal, but it would lock up on *Network Interface. Im not sure if it is a driver problem, a problem with my computer, or a bug in ubuntu. Thank you for your help. I will try the dhclient as soon as possable.

---

### Post by MrSt0ne on 2006-08-31
The Sudo Dhclient worked! Thank you very much for your help. Now how would I make it so that everytime on startup it will run this command?

---

### Post by cwaldbieser on 2006-08-31
> **MrSt0ne said:**
> The Sudo Dhclient worked! Thank you very much for your help. Now how would I make it so that everytime on startup it will run this command?

Normally. you should be able to configure it from the networking GUI by changing the wireless adapter properties from a static IP address to dynamic.

OR

edit /etc/network/interfaces and make sure the setting for your wireless adapter looks something like:

```

auto wlan0
iface wlan0 inet dhcp

```

HOWEVER, I am guessing that part of the problem you were facing has something to do with the driver not loading until after your system had completely booted.  I am not sure why that would happen.  You could just put a shortcut on your desktop that runs the dhclient command for you.

I am guessing that if you ask in the networking sub-forum, someone will probably have a better idea of what is going on.

Also, you shouldn't have to reinstall every time you get frozen-- you should be able to boot with some option to disable the network stuff, though I am not sure how to do that.

---

