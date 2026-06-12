---
title: "ip address"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by nousername on 2006-04-20
How do I findout what my ip address is on my local network?

Thanks

---

### Post by jorn on 2006-04-20
Type in terminal:
ifconfig
Inet addr is your address.
Jorn

---

### Post by Jason_25 on 2006-04-20
ifconfig at the terminal.  Or you can add the network monitor applet to the bar.

---

### Post by Nordoelum on 2006-04-20
How do I renew my IP in terminal? If the wired wosn't connected when I intalled server config.

---

### Post by Randomskk on 2006-04-20
From ifconfig you should have seen the device (often eth0), type:

sudo dhclient eth0

replacing eth0 with the device.
That will renew the IP with the DHCP server which I think is what you want.

---

### Post by Nordoelum on 2006-04-20
I didn't have a eth0 device in the ifconfig list :( Strange since I got an network card inside. And it found the card when installing.

I am using the server installation. Trying to install xubuntu.

---

### Post by Randomskk on 2006-04-20
type "lspci" (without "s) at console and put the output here, it should show if your network card is being picked up.

edit: did you have any IPs? anything at all reported by ifconfig?

oh, and if you don't have internet on the linux box I guess pasting lcpci would be hard, just look for the word "ethernet" in the output and say the text from those lines.

---

### Post by Nordoelum on 2006-04-20
[quote=Randomskk]type "lspci" (without "s) at console and put the output here, it should show if your network card is being picked up.

edit: did you have any IPs? anything at all reported by ifconfig?

oh, and if you don't have internet on the linux box I guess pasting lcpci would be hard, just look for the word "ethernet" in the output and say the text from those lines.[/quote]
Did a clean install with the cable connected. And I am now downloading Xubuntu.

Thanks anyway:D I migth need your advice in the future..

---

