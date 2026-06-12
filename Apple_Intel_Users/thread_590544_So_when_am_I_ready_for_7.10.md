---
title: "So when am I ready for 7.10?"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by subferno on 2007-10-24
I have the Santa Rosa MBP and tried setting up 7.10 for the last couple of days.

First, I have been trouble getting the wireless connection to work (Madwifi 2695). The interface is there but no websites get connected. Since I can't connect to the internet wirelessly, is there some big package or bundle of all the drivers I need to get the Santa Rosa running out of the box, not just for wifi? I can then burn it on a CD and not worry about getting my internet connection configured first.

Second, what is the deal with the screen blacking out for half a second everytime I hit the backspace key in the terminal or anywhere?

Third, what is this I hear about the CPU fan not running at the correct speed in Ubuntu? Is this something I have to configure myself?

---

### Post by alephsmith on 2007-10-25
I use madwifi 2497 and it works everytime.

The sceen blank is a visual bell (name?). I forget where the setting is, but it is in replacement of the system chime you would usually hear. Search in the config menu to disable it.

---

### Post by subferno on 2007-10-25
I have WEP 128 Hex enabled at home but Ubuntu never connects successfully. If I disabled the security then my internet works.

---

### Post by cyberdork33 on 2007-10-25
> **subferno said:**
> I have WEP 128 Hex enabled at home but Ubuntu never connects successfully. If I disabled the security then my internet works.
Someone else has a similar issue:
[http://ubuntuforums.org/showthread.php?t=591301](http://ubuntuforums.org/showthread.php?t=591301)

Can you try some other type of encryption? WEP really isn't that secure anyway.

---

### Post by subferno on 2007-10-28
I switched from WEP to WPA 1 Personal and have the same problem.

Disabling the encryption, my wireless connection works just fine. As soon as I enable it, I can't connect again.

---

### Post by cyberdork33 on 2007-10-28
can you verify how you are connecting?

In System > Administration > Network make sure that it says roaming mode is enabled and use network-manager to connect (in the top corner, near clock). If that was what you are using, sorry, I don't know what to tell you.

---

### Post by subferno on 2007-10-29
Its really weird though because switching over to WPA works sporadically.

If I manually configure the network, my MBP sees the network but never connects. If I set it to roam, it takes a while for the MBP to find a connection to the network and then prompts me for the password.

So I don't know why it works in roam mode and not manual.

---

### Post by cyberdork33 on 2007-10-29
> **subferno said:**
> Its really weird though because switching over to WPA works sporadically.

If I manually configure the network, my MBP sees the network but never connects. If I set it to roam, it takes a while for the MBP to find a connection to the network and then prompts me for the password.

So I don't know why it works in roam mode and not manual.
manual does not work because it doesn not support your encryption. You have to use the network-manager applet.

---

