---
title: "How do I get my IP address?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by viseversa on 2007-06-26
anyone?

---

### Post by Dylnuge on 2007-06-26
Go to the terminal. (Applications->Accessories->Terminal) Type

```
ifconfig
```

You will see a line that looks like this under either eth0 or eth1:

inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0

The number after Inet Addr is your IP.

PS: If it begins with 192.168, it is local. If it is local, you will need to contact your network administrator about port forwarding, since whatever you want it for won't work otherwise.

---

### Post by Rocket2DMn on 2007-06-26
If you are behind a router and want your public IP address, just go to a site like [http://www.ip-adress.com/](http://www.ip-adress.com/)
or google *my ip* for others

---

### Post by RAH66 on 2007-06-26
or right click on your system tray network monitor and then on connection information...

---

### Post by Dylnuge on 2007-06-26
> **RAH66 said:**
> or right click on your system tray network monitor and then on connection information...

Or, should you be using KDE, Manual Configuration. (The info is there, but you need to be root (using sudo, of course)).

---

### Post by ramjet_1953 on 2007-06-26
If you use Synaptic to download [COLOR="Blue"]giplet[/COLOR] (it's in the universe repository) it allows you to then put an ip display in either your top, or bottom panel. It can be configured to display your local, or Internet ip.

After downloading giplet, just right click on either your top or bottom panel and choose add to panel. When the window opens, giplet is in the Utilities section.

Once you have addet giplet to your panel, just right click on it, to configure it.

Regards,
Roger :cool:

---

### Post by Dylnuge on 2007-06-28
Once again GNOME specific...not to mention that the user only wanted their IP...unless it is dynamic, this seems overly complicated, since they probably only need it once.

---

### Post by speaker219 on 2007-06-28
If you want your outside IP address,
just simply go to: [http://whatismyip.com/](http://whatismyip.com/)

---

