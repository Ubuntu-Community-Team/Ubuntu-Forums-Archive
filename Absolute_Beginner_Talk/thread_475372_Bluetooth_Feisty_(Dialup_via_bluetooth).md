---
title: "Bluetooth Feisty (Dialup via bluetooth)"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-16
I followed [this]("http://yoonkit.blogspot.com/2007/05/ubuntu-dialup-via-bluetooth.html") guide here to try and see if I could use my mobile as a dial up modem.

When I got to here
> 
I set the computer bluetooth key using the bluez-pin utility

I do not know how to do this. Been searching the internet for awhile and cannot seem to find a straight answer.

Anyways I carried on. And followed the rest of the instructions.

When I get up to configuring wvdial, I get told to do so like this
```

[Dialer Defaults]
Phone = *99#
Username = maxis
Password = wap
New PPPD = yes
Dial Command = ATDT
[Dialer E61]
Modem = /dev/rfcomm0
Baud = 460800
Dial Command = ATDT
Init2 = ATZ
Init3 = ATM0
Init4 = AT+CGDCONT=1,"IP","unet"
FlowControl = crtscts
Modem Type = Analog Modem

```
Do I change *99# to the number of my ISP?


Anyways I carried on and try to connect but got this
```

$ wvdial E61
--> WvDial: Internet dialer version 1.56
--> Cannot open /dev/rfcomm0: Connection refused
--> Cannot open /dev/rfcomm0: Connection refused
--> Cannot open /dev/rfcomm0: Connection refused

```

During this I was asked for a pass code on my phone, I tried 1234, 0000 ,1111 none of these where correct.

Anyone got any ideas? I think it has something to do with bluez-pin or something.

Thanks

---

### Post by sKAApGIF on 2007-06-17
The proper way to pair:
[LIST=1]
[*]Open a console
[*]First Determine the MAC adress of your device.  Scan for all bluetooth devices by typing: hcitool scan into the console.  A list will appear with something like: 00:18:13:50:0C:EB YourDeviceName.  The Code is the devices MAC adress, to connect to it you will need this.
[*]Use the mac address to tell your computer which device to connect with.  Type: hcitool cc XX:XX:XX:XX:XX:XX  (where the X's represent your device's mac adress)
[*]Now authenticate (or pair / enter pins) your device with your computer by typing: hcitool auth XX:XX:XX:XX:XX:XX (again use the MAC adress as obtained in the 2nd step)
[*]A screen will pop up asking for a pin, enter the same on your phone and your computer and you should be done :)
[/LIST]

"Do I change *99# to the number of my ISP?" 

No *99# isn't a real number, it's called a data profile.  I'm not sure which to use, seems like different phones or phone companies require different profile numbers.  I for instance use *99***1#.  But your mobile company should be able to tell you what the number is.  Else experiment with either *99# or *99***X# where X is any integer between 1 and 4.  Why this is so I'm not sure anyone else have an idea about why there's different "numbers" to enter?

"--> Cannot open /dev/rfcomm0: Connection refused"
As you say this is probaply because of the pin.  If you've paired the computer and device and still get this error it means somehow your device isn't connected to rfcomm0.

Though I think after pairing it'll be all good.
Good luck.

---

### Post by thinkgeek on 2007-06-21
I've been trying to pair my phone and I followed the instructions mentioned above. The problem comes in at step 5. The box pops up on my computer and I enter a pin, but nothing happens on my phone and after a little while the connection is timed out. Do I have to use a pin that is already stored on my phone (such as one entered while setting it up with windows), or is there something else going on here?

Any ideas?

---

### Post by guysmiley25 on 2007-06-22
Peering really does seem to be a bitch! And I very jealous of anyone who has got this working!!!

I have been successful in using my cellphone as a dial up modem, and using blue tooth to trasher files.
But this still does not work.

hcitool ccXX:XX:XX:XX:XX:XX
 Waits for awhile and then returns the prompt

hcitool auth XX:XX:XX:XX:XX:XX
 Returns an error, I'm at a different machine at the moment and cannot remember it.

So sorry thinkgeek, I have not ever seen this pop up you speak of!


So does anyone know whats happening?

Also I'm using Xubuntu Feisty is that makes a differences

Thanks

---

### Post by dvo on 2007-06-23
This is how I got the PIN popup working: call (even as a normal user)
```
passkey-agent --default /usr/bin/bluez-pin
```
before initiating the connection. This will register bluez-pin as the pin helper,
as you may check with ```
tail -f /var/log/syslog
```

N.B. Including in /etc/bluetooth/hcid.conf a line like
```
pin_helper /usr/bin/bluez-pin;
```
does not help anymore - for some reason, this option is not recognized any more :(

---

