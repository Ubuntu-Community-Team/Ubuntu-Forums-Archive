---
title: "Internet not working"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by geoffphuket on 2006-10-14
I have no internet connection using my Hyundai Hase-270 ADSL modem - connected via the LAN socket on my laptop.

Does anyone know if it's supported by Ubuntu?

---

### Post by dmizer on 2006-10-14
> **geoffphuket said:**
> ADSL modem - connected via the LAN socket on my laptop.

okay ... i want to clarify something here.  is this what you have?

phone cord -> adslmodem -> lan cable -> pc

and not

phone cord -> adslmodem -> usb cable -> pc

?

if so, the problem is not getting drivers to your adsl modem, but configuring your network card.

---

### Post by geoffphuket on 2006-10-15
> **dmizer said:**
> okay ... i want to clarify something here.  is this what you have?

phone cord -> adslmodem -> lan cable -> pc

and not

phone cord -> adslmodem -> usb cable -> pc

?

if so, the problem is not getting drivers to your adsl modem, but configuring your network card.

Yes .....  Phone cord -> adslmodem -> lan cable -> pc

[COLOR="Red"]NOT USB[/COLOR]

So I have to configure my networl card ? How do I do that ?

---

### Post by NeoLithium on 2006-10-15
Can you copy and paste the results of this:
```

ifconfig

```
And what type of connection do you have? Do you require to enter your username and password to log on to your ISP or just plug and play?

---

### Post by geoffphuket on 2006-10-15
> **NeoLithium said:**
> Can you copy and paste the results of this:
```

ifconfig

```
And what type of connection do you have? Do you require to enter your username and password to log on to your ISP or just plug and play?

No - P&P

---

### Post by NeoLithium on 2006-10-15
What was the result of ifconfig? Were you able to see eth0 on the list that it produced?  And just so I don't give you any dumb suggestions, have you already tried running pppoeconf?

---

### Post by geoffphuket on 2006-10-15
I should have said, I'm running Ubuntu direct from the Live CD and  logged on to the internet via Windows Xp at the moment, so it's difficult pasting ifconfig results. However, the connection appears to be live and I have eth0....but Firefox refuses to download anything. 

Those kind enough to answer my questions will have to bear (bare? :D ) with me whilst I reboot the PC

---

### Post by geoffphuket on 2006-10-15
> **NeoLithium said:**
> What was the result of ifconfig? Were you able to see eth0 on the list that it produced?  And just so I don't give you any dumb suggestions, [COLOR="Red"]have you already tried running pppoeconf?[/COLOR]

No...How do I do that?

---

### Post by geoffphuket on 2006-10-15
Back in 15 minutes...rebooting with Ubuntu to try the above ideas.

---

### Post by NeoLithium on 2006-10-15
As well, there is a good article here to help out with networking setup in ubuntu.
[http://www.ubuntuguide.org/wiki/Dapper](http://www.ubuntuguide.org/wiki/Dapper)

---

### Post by dmizer on 2006-10-15
i don't think you're pppoe, so pppoeconf shouldn't do anything.

if you were pppoe, you wouldn't be able to ping.

have you tried adjusting firefox's settings as i described above?

---

### Post by geoffphuket on 2006-10-15
[COLOR="black"][COLOR="Red"]I'm on line with Ubuntu [/COLOR][/COLOR]:D :D - thanks for the help dimizer and NeoLithium.
configering the network card  and changing the preferred DNS server settings did the trick.

Now I've got to figure out how to change the screen resolution...my grandmother could see the font I've got from a mile away!!  ...preferences > screen resolution only shows 3 choices and the one I want isn't an option. I'm running a 19'' LCD from my laptop.

---

### Post by dmizer on 2006-10-15
> **geoffphuket said:**
> Now I've got to figure out how to change the screen resolution...my grandmother could see the font I've got from a mile away!!

take a look at the output of lspci.  make a note of what your video card is.

then do:
```
sudo dpkg-reconfigure xserver-xorg
```
make sure all settings are configured correctly regarding both monitor and video card.  just leave the rest of the settings at default (keyboard, mouse, etc).

---

