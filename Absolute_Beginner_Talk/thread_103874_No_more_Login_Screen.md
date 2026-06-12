---
title: "No more Login Screen"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-14
hey... i no longer have a login screen.. when i boot into linux... it boots right into KDE without asking me to login. but when i log out to switch from kde to gnome... my keyboard no longer works... but when i restart X... everything i typed is in the command line.. 

Can someone help me get it to work again... Thanks

~Lance

---

### Post by My8os on 2005-12-15
[QUOTE=noob_Lance]
hey... i no longer have a login screen.. when i boot into linux... it boots right into KDE without asking me to login....
[/QUOTE]

Type in konsole:
```

sudo systemsettings

```

Go to **System Administration->Login Manager->Convenience** and dis-enable *Auto-Login*

Hope it works :) .

---

### Post by noob_Lance on 2005-12-15
hm.... well...My8os... i love you lol... it worked... which really makes No sence... i never had auto-login enabled for me before..... :S

but now how do i tell my wireless card which networks to connect to... like ones that i know and am only ever around.... my neighbour has a wireless router... and my laptop always connects to it before it will find my own router.... helo :'(

thanks
~Lance

---

### Post by kaamos on 2005-12-15
Try setting the essid in /etc/network/interfaces. Here is my wlan configuration. Your interface might be different (eth1 or whatever)```
iface wlan0 inet dhcp
wireless_mode managed
wireless_nick ubuntu
wireless-essid **essid_here**
```

---

### Post by kingsidy on 2005-12-15
you can also get gtkwifi. Add the one you use the most to your preferred list. that might help

---

