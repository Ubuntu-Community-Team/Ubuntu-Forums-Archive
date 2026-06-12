---
title: "dhcp server drops database connection"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2007-09-10
I am in a library and all the PC's currently use a fixed IP except those connecting to the wireless network. For that we want to use a linux dhcp server. We have a 7.04 Ubuntu LAMP server with dhcp3 installed an assigning IP addresses outside of the static range assigned to the desktops, however usually within 10 minutes of plugging it into the network our Information Portal on port 5000 goes down. Internet traffic works fine, just traffic to that portal server on that port. Ideas?

---

### Post by Stormspace on 2007-09-10
Update: It appears as if the wireless bridges we were using for AP's was causing an issue with the DHCP server. Not certain what, but once they were removed the issues vanished. Unfortunately we now need another wireless solution. :)

---

