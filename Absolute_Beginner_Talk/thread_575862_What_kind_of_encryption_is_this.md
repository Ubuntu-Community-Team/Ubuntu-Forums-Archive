---
title: "What kind of encryption is this?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-10-14
Hi!
I installed Ubuntu on my girfriend's laptop a week ago when she visited me, and the wireless network worked fine. Now she's back home, but the laptop won't connect. It seems like she tries to use the wrong kind of encryption. The code consists of seven digits, one letter and two more digits. I told her to choose 64 bit hexadecimal, but the browser only keeps searching for the website, and nothing happens. Any idea where to start?

---

### Post by danpre on 2007-10-14
> **Joakim Stokland said:**
> Hi!
I installed Ubuntu on my girfriend's laptop a week ago when she visited me, and the wireless network worked fine. Now she's back home, but the laptop won't connect. It seems like she tries to use the wrong kind of encryption. The code consists of seven digits, one letter and two more digits. I told her to choose 64 bit hexadecimal, but the browser only keeps searching for the website, and nothing happens. Any idea where to start?

WEP with 64bit hex key uses 10 characters, and for WPA you can use a key with 10 characters.

Try to switch to WPA.

---

### Post by Joakim Stokland on 2007-10-15
Thanks, but it didn't work. We have now tried the different choices, but with no luck. The man who owns the router has told that it is a 64 bit code, and we have ensured that the code is the correct one. We have tried both manual configuration and roaming mode, but the nm-applet still shows the two computers with the cross.
Also, today she was logged on to the wireless network at school.
AND we have tried this:
```
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

Any further tips?
Thanks

---

### Post by ghost_ryder35 on 2007-10-15
wep 2 or wpa 2 ?

---

### Post by Joakim Stokland on 2007-10-15
She just called me and told that the internet is working. Downloading updates at this moment :D I'm not sure, but bad reception may have tricked us. I do think that WEP was the last setting she chose. I've told her to leave the settings the way they are now, and then we'll get back to it when I come visiting again :)

Thanks anyway for your help! :)

---

### Post by Joakim Stokland on 2007-10-18
It seems like the bad reception actually is a dying network card. The connection has been coming and going, and now she's nearly never able to connect. Any idea how we can check whether it is working properly or not? This is really driving me insane! It has come to the point where I consider letting Windows re-unite with her computer, just to see if the wireless card works under Windows. I actually can't imagine that Linux is the cause here, but I'm getting quite desperate. The connection varies from zero to thirty, or even full reception, and back to zero. She has been able to view only a couple of sites the last few hours...
She's gonna call Dell's technical support tomorrow, as it is a matter of warranty if it is defective hardware.
One other thing I find strange is that her local network doesn't show up when she plugs in a USB-network card that she borrowed from her mother. One of her neighbour's network shows up, but not the one she wants to connect to. But perhaps there's a less powerful antenna in the "dongle"?
Any ideas?
ANYTHING will be REALLY appreciated!
Joakim

---

### Post by Joakim Stokland on 2007-10-26
Can anyone please help me with this? She has tried different networks now, and her computer is able to connect to two of the four she tried. How on earth is this possible? I'm not absolutely sure, but I think one of the networks she was not able to connect to was open, and the other encrypted. Likewise one of the networks she connected to was open, and the other encrypted. I see absolutely NO reason why it should be like this, other than a dying wireless card, coming and going...

Anyone?
Thanks, Joakim

---

### Post by Joakim Stokland on 2007-11-03
Okay! I am back home now, and have been trying to get the card working. It is SO much easier to figure out what's wrong when I've got the computer in front of me instead of over the phone!
And this is what's wrong: BCM4318. You MAY have heard of it before; our dear Broadcom wireless card...

So now I'm reading many different threads about this same issue, but most of them regard this same card, but with 7.04 or earlier. She is running 7.10.
So before I install XP for her or buy her a PCMCIA card (just to keep her away from Microsoft ;) ) I will try to get this Broadcom-thing to work as it should.

Any help will be greatly appreciated!
I brought my router home, and her computer works as a charm connected to it, with encryption. MY computer connected flawlessly to the network where she lives. (And the key WAS 64 bit WEP, just for the record)

Does anyone know why the Broadcom card only works with some routers? And does anyone have ANY idea how I can get this thing on the net?

Thanks!
Joakim

---

