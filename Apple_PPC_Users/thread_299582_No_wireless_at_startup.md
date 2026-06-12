---
title: "No wireless at startup"
date: 2006-11-14
forum: Apple PPC Users
---

### Post by h.ornstein on 2006-11-14
After I had updated Dapper to Edgy the network settings are gone every time I startup. I have to change "automatic" into "static IP address" in Properties Wireless connection. Then OK and then do it all again but the other way around, thus "static" becomes "automatic". OK, and the connection is made.
This is really frustrating and did not happen in Dapper.

How can I make Network settings to remember the input.

Thanks for any help.

---

### Post by justplayin on 2006-11-15
Try to edit the network settings through
```
sudo gedit /etc/network/interfaces
```
That's where your network settings are stored.
To have dhcp for my ethernet connection I have a section
```
auto eth0
iface eth0 inet dhcp
```

After making a backup of the existing /etc/network/interfaces you can edit it, save it and do a
```
sudo /etc/init.d/networking restart
```
to see if anything has changed.

Have a look at [this.]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

Ok, I see, that you need to comment out any entry in /etc/network/interfaces exept the lo device, because network-manager puts his settings somewhere else. Refer to the wiki for info on this.

---

