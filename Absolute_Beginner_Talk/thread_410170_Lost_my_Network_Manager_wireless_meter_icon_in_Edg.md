---
title: "Lost my Network Manager wireless meter icon in Edgy"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by leftybob on 2007-04-15
I am using Network Manager to control my wireless connection in Edgy because it has WPA capability.
It works great, but I accidentally deleted my little blue ramp signal meter.  It is not available in the standard panel addons, and I don't have Network Manager listed under the applications menu.
The only way I could manually reconnect to the wireless network was to right click the meter and pick my network.  How can I salvage the meter?
Thanks

---

### Post by zvacet on 2007-04-15
```
sudo aptitude install network-manager
```

or

```
sudo aptitude install network-manager-gnome
```

---

### Post by leftybob on 2007-04-15
Sorry, I didn't explain well enough.   The program is on the computer and is working, I just lost my GUI meter interface, so if the wireless happens to not come up, I will have nothing to click on to restart the connection.
Hope that makes sense.
Thanks again

---

### Post by zvacet on 2007-04-15
```
whereis network-manager ls
```

This command will show you all directories and folders with network manager.In some of them probably is GUI too.

---

