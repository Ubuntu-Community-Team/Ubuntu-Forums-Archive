---
title: "wifi has trouble connecting after reboot/awake"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by TonySmash on 2007-05-29
i remember seeing a thread about this a few days ago but it has since disappeared into oblivion...

anywho, now that my wifi (airport extreme) is working, ubuntu decided to throw me another problem. if i reboot the machine or put it into a suspended (sleep) state and then wake it up, the wifi connection is gone and has a ridiculously hard time reconnecting. i even had a whole method for making it work - boot up, attempt to connect and fail, sleep, wake up, attempt to connect and fail, log off, log in, attempt to connect and *maybe* succeed. 

at any rate...this is a pain. has anyone else experienced something similar and have a solution? i'm sure i just have to tweak something...

btw i'm running feisty on an ibook g4 w/ airport extreme and the only thing i could think would cause problems is my wireless (2.4ghz) mouse.

---

### Post by scrooge_74 on 2007-05-29
I have similar problems to you in some instances it worked again by making changes to /etc/network/interfases

and leaving the wireless card in automatic

auto eth1
iface eth1 inet dhcp

that will fix it (sometimes) without rebooting

---

### Post by TonySmash on 2007-05-30
scrooge -

all those settings, unfortunately, were already set. so that wasnt my problem.

seriously, can ANYONE get their wifi on a 12" ibook g4 to work perfectly? please?

---

