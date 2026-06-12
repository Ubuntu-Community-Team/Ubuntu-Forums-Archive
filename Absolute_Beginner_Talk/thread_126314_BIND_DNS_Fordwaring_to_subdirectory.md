---
title: "BIND DNS Fordwaring to subdirectory?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by gwfire on 2006-02-06
Im using ubuntu and set up a dns server with bind. 

i'm runnning with my server a groupware (php+mysql). now i want, that i can enter "intranet" inside the browser and the system automatically jumps to a defined subdirectory (e.g. my groupware)

is that possible??

---

### Post by alamba on 2006-02-06
Yep. You'll need to set up a DNS within your network and have forwarders to your ISP DNS for external resolution. All internal clients will now need to use this internal DNS for name resolution.

Think there is an easier way by adding an entry into your hosts file. This will take you to your web server though not sure if it'll take you to a specific subdirectory.

Akshay

---

### Post by gwfire on 2006-02-06
[QUOTE=alamba]Yep. You'll need to set up a DNS within your network and have forwarders to your ISP DNS for external resolution. All internal clients will now need to use this internal DNS for name resolution.

Think there is an easier way by adding an entry into your hosts file. This will take you to your web server though not sure if it'll take you to a specific subdirectory.

Akshay[/QUOTE]


THX for the fast answer - but i'm a newbie - where can i find the hosts file and what will i have to change?

---

### Post by alamba on 2006-02-07
vi /etc/hosts
You'll need to add a entry for the server with its IP and a name for it. Like I said before this will resolve the IP to the host and hence take you to the host but might not take you to a specific sub directory.

A

---

