---
title: "Keep iwconfig changes...."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-28
iwconfig doesn't keep the changes I've made to the configuration when I restart my computer. How do I keep the changes? Is there a file I need to edit?

More specifically I have added a physical address for my access point using the folowing:
sudo iwconfig ra0 ap [my address]
but iwconfig doesnt keep the changes on restart.

Which file would I need to edit?

---

### Post by popkid on 2006-05-28
I think you will need to add a couple of lines to your /etc/network/interfaces file

as below

auto ra0
iface ra0 inet dhcp

pK

---

