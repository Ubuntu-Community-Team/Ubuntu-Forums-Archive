---
title: "Reconnecting to internet without restarting (ADSL)"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2006-12-16
Hello all

I am using Ubuntu 6.06 with a speedtouch USB modem to connect to my UK based ISP. The [SpeedTouch Howto]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch") worked fine once I realised that in the UK, the VP.VC values are 0.38 and that Orange/Wanadoo use PPP over ATM, and that the 'username' has to have @fs on the end. It didn't take too long ](*,) . It is also worth mentioning that my SpeedTouch 330 is version 4 but in a black mouse like case. The firmware name string has changed and only has THOMSON now.

Now I want to be able to disconnect and reconnect the internet as and when and not have to restart the laptop each time. Disconnecting is easy if not elegant - just pull the USB cable out. Reconnecting has defeated me so far. Any pointers? Ideal would be some way of having a little icon that you click, but for now a terminal command would do.

Cheers

EDIT: corrected the title spelling :-#

---

### Post by Ecthelion on 2006-12-16
If you have the network app docked in a panel, then just click on it, say "configure" and then uncheck the box before your network connection to disconnect and check it to connect again.

---

### Post by keithpeter on 2006-12-16
> **Ecthelion said:**
> If you have the network app docked in a panel, then just click on it, say "configure" and then uncheck the box before your network connection to disconnect and check it to connect again.

Thanks for this response. 

The network icon in Gnome shows two entries; ppp0 and Io. ppp0 seems to detect packets coming in and out, and the 'support' tab shows the IP address allocated to my computer by my ISP correctly. There is no checkbox to uncheck. 

When I click the 'configure' button, the 'deactivate' button is greyed out, and the modem connection claims not to be configured. See the screen grab attached to this post.

Any other suggestions about where to look appreciated.

---

### Post by Ecthelion on 2006-12-16
Hmm, try this:

Click on the network app, change the name to **eth0**
Does it detect packages being send / recieved?
If yes, then do again "configure" an d check uncheck as you want.

If not, please post the output of ```
ifconfig
```

---

### Post by keithpeter on 2006-12-16
> **Ecthelion said:**
> Hmm, try this:

If not, please post the output of ```
ifconfig
```


```

          keith@xylem:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21433 (20.9 KiB)  TX bytes:21433 (20.9 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:84.70.XXX.XXX  P-t-P:62.25.XXX.XXX  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:99187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:143932622 (137.2 MiB)  TX bytes:3475534 (3.3 MiB)

```

Hello Ecthelion, here is the ifconfig command output. Thanks for getting involved with this one.

---

### Post by Ecthelion on 2006-12-16
I don't know much about "Point-to-Point Protocol", I'm afraid.

Maybe you can try this to reconnect:

```
 sudo /etc/init.d/networking restart 
```

If this doesn't work then I've no idea how to help.

---

### Post by DRGuy on 2006-12-16
I'm no expert - so take this with a grain of whatever...

If I pull my ethernet cable, and then attach it again (or if I boot the machine without the ethernet cable and then connect it later) I can get the ethernet working again with an:

ifdown eth0
ifup eth0

I don't know if that works for ppp.

Hope that is of some help, good luck,
--
DRGuy

---

### Post by keithpeter on 2006-12-17
> **DRGuy said:**
> 
ifdown eth0
ifup eth0


[QUOTE=Ecthelion]
sudo /etc/init.d/networking restart
[/QUOTE]

Neither of these worked directly, but I did take the spirit of these suggestions and actually *read* the bootscript instead of typing it in like an incantation :) 

If you boot the laptop without the USB modem connected and then connect the USB modem, the command below will start the ppp over atm connection.

```

sudo pppd call speedtch

```

And I [found a thread that mentioned how to drop the connection]("http://ubuntuforums.org/showthread.php?t=199347&highlight=how+to+stop+pppd") by killing the pppd daemon.

```

sudo killall pppd

```

That has saved me a few reboots per day now! I should explain this laptop has only one USB port and the modem does not like sharing using the passive 4 usb port box I bought. 

[QUOTE=Ecthelion]
I don't know much about "Point-to-Point Protocol", I'm afraid.
[/QUOTE]

I don't know too much about anything in Linux so you are (both) way ahead. 

If anyone knows of a nice little panel applet that can start and stop pppd in a clean way without the user having to know the root password, please share!

---

