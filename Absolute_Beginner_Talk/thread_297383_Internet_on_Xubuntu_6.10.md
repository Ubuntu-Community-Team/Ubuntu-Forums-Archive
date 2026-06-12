---
title: "Internet on Xubuntu 6.10"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Nameless One on 2006-11-11
I am a newbie to Ubuntu, having only just installed it today.
Everything is running fine except for the Internet.
I managed to get Firefox working by changing the 'network.dns.disableIPv6' value under 'about:config' from false to true.
But nothing else other than Firefox can connect to the internet.
I run Xubuntu 6.10 alongside Windows. In Windows, everything connects perfectly to the internet, and I can access it through an old Mandrake LiveCD.
I have a 'D-Link DSL-502T' ADSL Router connected via Ethernet to my nForce something network card.

---

### Post by 3rdalbum on 2006-11-11
Give this a whirl:

Go to the terminal and type:

```
gksudo gedit /etc/modprobe.d/aliases
```

Type your password when asked. In the text file that opens, find the line:

```
alias net-pf-10 ipv6
```

Change it to:

```
alias net-pf-10 off
```

Save the file, exit the editor, and write down somewhere what you've done in case you need to revert back (you shouldn't need to though). Now reboot, and things should now be working for you.

If it doesn't, go back into the file and change the line to:

```
alias net-pf-10 off ipv6
```

Good luck.

---

### Post by Nameless One on 2006-11-11
I tried changing ```
alias net-pf-10 ipv6
``` to both ```
alias net-pf-10 off
``` and ```
alias net-pf-10 off ipv6
``` but unfortunately I still cannot get Gaim or Synaptic to connect to the internet.

Firefox still runs fine, but I have to type ```
sudo dhclient eth0
``` into the terminal before I can go online with Firefox.

Edit: I tried ```
alias net-pf-10 ipv6 off
``` but that didn't work either. Would removing the line help? Perhaps the problem lies elsewhere.

---

