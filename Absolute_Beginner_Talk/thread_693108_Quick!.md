---
title: "Quick!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-02-10
Quick, please! How do I start the network manager (so I can connect to a new network I've never connected to)?  I don't have a system tray and I can't remember the terminal command!

---

### Post by spiderbatdad on 2008-02-10
create a notification are by right clicking on the panel and add to panel. Then Alt-F2 and run **nm-applet**

---

### Post by beercz on 2008-02-10
System->Administration->Network?

---

### Post by cartisdm on 2008-02-10
> **beercz said:**
> System->Administration->Network?

That doesn't give me any option of where to access the local networks, unless I'm missing something......

---

### Post by beercz on 2008-02-10
> **cartisdm said:**
> That doesn't give me any option of where to access the local networks, unless I'm missing something......
Places->Network?
or
Places->Connect to server?

What exactly are you trying to do?

---

### Post by Majorix on 2008-02-10
```
gksudo network-admin
```
Tab is your friend ;)

---

### Post by cartisdm on 2008-02-11
> **beercz said:**
> What exactly are you trying to do?

I'm trying to access my wireless connections, I'm still not getting where I need to be....:-/

---

### Post by JoshuaRL on 2008-02-11
```

gksu network-manager

```
I'm guessing?

---

### Post by cartisdm on 2008-02-11
> **JoshuaRL said:**
> ```

gksu network-manager

```
I'm guessing?

nothing opens up. maybe it's opening to my system tray? (it's permanently hidden)

---

### Post by jordanmthomas on 2008-02-11
If you don't have a system tray, you will not be able to access the network manager applet.
Spiderbatdad suggested what you should do; you can always disable the notification area again when you're done.

If you're not willing to use a notification area, you can always configure your wireless network manually.
```
sudo iwconfig [COLOR="Blue"]eth1[/COLOR] essid [COLOR="Red"]yourssid[/COLOR]
```
Where eth1 is your wireless interface and yourssid is the essid of the network you'd like to connect to.  If you need encryption or whatever, look at iwconfig's help.

Once your network is configured, grab an IP
```
sudo dhclient [COLOR="Blue"]eth1[/COLOR]
```

---

### Post by cartisdm on 2008-02-11
> **jordanmthomas said:**
> If you don't have a system tray, you will not be able to access the network manager applet.
Spiderbatdad suggested what you should do; you can always disable the notification area again when you're done.

If you're not willing to use a notification area, you can always configure your wireless network manually.
```
sudo iwconfig [COLOR="Blue"]eth1[/COLOR] essid [COLOR="Red"]yourssid[/COLOR]
```
Where eth1 is your wireless interface and yourssid is the essid of the network you'd like to connect to.  If you need encryption or whatever, look at iwconfig's help.

Once your network is configured, grab an IP
```
sudo dhclient [COLOR="Blue"]eth1[/COLOR]
```

Awesome, this will work best for what I need to do. Thanks!

---

### Post by dasunst3r on 2008-02-11
I suspect that you may have removed your system tray.  Try right-clicking on the panel, clicking Add to Panel, selecting "Notification Area," and clicking "Add."

---

### Post by cartisdm on 2008-02-11
> **dasunst3r said:**
> I suspect that you may have removed your system tray.  Try right-clicking on the panel, clicking Add to Panel, selecting "Notification Area," and clicking "Add."

Don't have a panel :D

See below

---

### Post by jordanmthomas on 2008-02-11
nice, looks like you got connected too?
Also, I don't like gnome-panel either (and thus don't run gnome), but you could probably add a system tray applet to AWN and then run 
```
nm-applet
```
Personally, I use pypanel when I'm in need of a tray.

---

