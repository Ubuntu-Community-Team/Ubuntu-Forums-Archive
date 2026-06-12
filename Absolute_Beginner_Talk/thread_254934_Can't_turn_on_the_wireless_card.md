---
title: "Can't turn on the wireless card"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by lintroduccion on 2006-09-10
I'm using a Dell Inspiron 6400 laptop. I installed the Xubuntu 6.06 LTS last weekend and updated everything:)... But suddenly, I can't get my wireless card (Intel PRO Wireless 3945ABG) to work.

The network setting shows that I do have a LAN card (eth0) and a wireless card (eth1). All that I have to do is to turn it on with FN+F2 key... which DOESN'T WORK! It works well in Windows XP.

I read that my wireless card should work out of the box in Ubuntu, so maybe there's a problem with my keyboard driver, instead? It's strange, because other FN key functions like increase or decrease screen brightness works perfectly.

I'm stuck. I don't have a LAN cable at home so the only way to connect is by the wireless network, with a wireless card that I can't turn it on... I can't install or update anything on my Ubuntu partition. Help!!!


P.S: The Wi-Fi LED "blinks" when booting Ubuntu, as if they were "trying" to turn on. It doesn't blink at all when I boot Windows XP.

---

### Post by lintroduccion on 2006-09-10
Oh, and by the way, I installed and updated my Xubuntu installation at work, where there is a LAN cable to connect it. I didn't check my wireless card then, assuming that it would work at home as expected:-? . Same for the the FN+F2 key ](*,) ...

---

### Post by furiousV on 2006-09-10
What does "iwconfig" return?

See if ```
ifconfig wlan0 up
``` does anything at all.

Are you using an encrypted wireless network?

---

### Post by UltraMathMan on 2006-09-10
Had the same problem (Inspiron E1505 same wireless card) booting into XP then Ubuntu fixed it for now. If what happened to me is happening to you everything is installed and detected but the hotkey mysteriously stopped working. Sorry I can't offer you quick solution but if I find something I'll let you know :)

---

### Post by MarkSheely on 2006-09-10
If it blinks when you're booting, then its on.  I think you are having a different problem.  It definitely isn't a keyboard problem.  

What you're describing would happen if you are trying to connect to a different network than the network you were previously connected to, but haven't changed your settings for the network you are currently trying to connect to.   The blinking light lets you know your card is activiated but not connected to a network yet.  

--Mark

---

### Post by lintroduccion on 2006-09-10
Finally, It's working! I just had to open the network-manager, open my wireless card preferences and choose the connection I wanted. The wi-fi led turned on and everyone's happy:p .

[[IMG]http://img172.imageshack.us/img172/199/2nf0.jpg[/IMG]](http://imageshack.us)

I checked the FN+F2 combination. It works, but only works when turning off the card, and that's it. "eth1" dissapears from the list and in order to have my wi-fi back I would have to reboot to Windows XP, turn on the card by FN-F2 and then reboot into Xubuntu. Quite annoying...


furiousV>
I'm not using an encrypted connection.
iwconfig returns this:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"USR8054"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E5:83:42
          Bit Rate:11 Mb/s   Tx-Power:14 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/100  Signal level=-83 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:916   Missed beacon:0

sit0      no wireless extensions.
```

"ifconfig wlan0 up" tells me there's no such a device.

UltraMathMan>
Now we have to figure out how to get it to work the other way](*,) ...

Mark>
Thanks. I learned something new today.:-D

---

### Post by UltraMathMan on 2006-09-10
Yeah the problem is, it's working so I don't go rushing about looking for a solution until it breaks :)

---

### Post by UltraMathMan on 2006-09-22
lintroduccion > Ok, so it's misbehaving again, I'm continuing my attempts to get it working [here]("http://www.ubuntuforums.org/showthread.php?t=246074") so if I find anything (or anyone else does) that's probably where it will be.

---

