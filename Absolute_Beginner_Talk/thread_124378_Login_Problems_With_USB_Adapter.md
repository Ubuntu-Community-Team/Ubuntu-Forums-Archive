---
title: "Login Problems With USB Adapter"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by LinuX Nova on 2006-02-01
Hey everyone,

Last night, I finally managed to get my NETGEAR USB Wifi adapter up and running with ubuntu, and after having a bit of a play aroud on the internet, i decided to change a colour on my login screen. When i had done this, I logged out of my user, intending to log back in using the same username just so that i could see my new login screen.

Unfortunately, this tale has a twist, and after i had entered my username and passowrd and clicked to log in, the welcome screen vanished, as usual, and i was brought to a brown empty screen, as usual, except in this case, i was on this screen forever, and the little ubuntu rectangle "loading" thing didn't appear, nor did anything else. Well, i left it for a couple hours and returned to find the same screen. Fearing for the worst, i restarted my computer and waited until the welcome screen appeared, and typed my user details in again. Well, the same thing happened again, and a thought struck me.

I removed my Wifi USB adapter and restarted my computer, typed in user, password and clicked login, and it worked, it logged on and everything worked.

This means that my usb adapter is the problem doesnt it?

Does anyone know haw i can stop this from happening?

Thanks in advance,

Paul.

---

### Post by rooster on 2006-02-01
Alittle workaround (maybe) could be to boot without USB-wifi-adapter and then, after login, stick it in the USB-Port.

Is this working? Can you use it then?

---

### Post by LinuX Nova on 2006-02-01
How would i activate it after sticking it in after login?

(what would i type in the terminal?)

Thanks.

---

### Post by rooster on 2006-02-01
[QUOTE=LinuX Nova]How would i activate it after sticking it in after login?
[/QUOTE]

Normally, if hotplug is working, it should be detected automatically.

---

### Post by rooster on 2006-02-01
And after that you can configure your network to not use ethernet but wlan.

But it is only meaningful if you don't need DHCP over WLAN for your network configuration (DHCP gives your computer the IP adress and you often have a DHCP-server in a DSL-router).

---

### Post by nijinsky on 2006-02-01
[QUOTE=LinuX Nova]How would i activate it after sticking it in after login?

(what would i type in the terminal?)

Thanks.[/QUOTE]

sudo ifup wlan0

I have found that botting is talled by hotplug and my usb wifi. I moved back to windows because of this and my computer being a bit tempremental and rebootin all the time (hardware not SW). When I ge tit up I'll try ubuntu again. 

Mind you I never got network printing to work either.

cheers
bob

---

### Post by LinuX Nova on 2006-02-01
Yes, that works, thank you nijinsky.

But... does this mean i have to do this everytime i log in? Cos that's not very convenient.

---

### Post by LinuX Nova on 2006-02-01
...anyone?

---

### Post by rooster on 2006-02-03
Hi Linuxnova,

sorry, I can't help you any further with it. But now you know how it's working. Maybe a workaround could be to write a script wlanstick_up with an editor:
```

#!/bin/bash
sudo ifup wlan0

```
make it executable with ```
chmod +x wlanstick_up
``` and, when laid on the desktop, you can doubleclick it after inserting your USB-stick.

But I'm sure someone else even has a better idea!

Rooster

---

