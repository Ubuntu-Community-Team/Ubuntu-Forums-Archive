---
title: "Where on Earth has Network Manager installed to?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-04
Hello hello,

Can anyone tell me how I run network-manager please? 

I'm a laptop user using WPA encryption on my wireless network - I wanted network-manager not only to make full use of WPA, but also to make it easy to switch betwen various wireless networks (which I do a lot when I'm at university).

As of now, I have installed network-manager through Synaptic (just can't seem to find it!), my wireless card is all correctly installed, and I can connect to unsecured networks with no problems whatsoever (I could do that before without network-manager anyway).

Thanks.

---

### Post by Jagot on 2006-08-04
Hit alt+f2 and type nm-applet.

---

### Post by FizDev on 2006-08-04
Try installing the gnome front-end.. Type in a terminal (I think it's that)
```
sudo apt-get install network-manager-gnome
```

---

### Post by Jagot on 2006-08-04
When you install network-manager it pulls network-manager-gnome with it.

---

### Post by FizDev on 2006-08-04
Oh, sorry =S didn't know... thanks for the info ;)

---

### Post by cheway on 2006-08-04
I just installed network-manager - I just checked Synaptic, and the network-manager-gnome (is this the GNOME frontend you're referring to?) is not installed.

---

### Post by cheway on 2006-08-04
...and when I do the alt-F2 business and type nm-applet, I get the error message...

> Could not open location 'file:///nm-applet'

Details: The location or file could not be found.

network-manager is definitely installed.

---

### Post by Jagot on 2006-08-04
Hmm - thought it was a dependency - go ahead and download it.

---

### Post by cheway on 2006-08-04
Ok chaps, I installed the GNOME front end, and it popped up in my system tray (saying I had a wired connection, which I do right now while I mess around with this wireless). I also had the OPTION of wireless as well.

Anyway, I then disconnected the ethernet, and reset my machine - upon restarting, there are no wireless options at all!! What's going on?!

---

### Post by cheway on 2006-08-04
Ok, at the moment, I have disabled the encryption on my router - the network is unsecured.

The wireless is now working again like it was before, BUT the network manager icon has a red line through it - it doesn't matter if the 'enable networking' option is checked or unchecked, it always looks the same.

It seems I can't even use network-manager on an unsecured wireless network, let alone a WPA encrypted one! Any ideas?

---

