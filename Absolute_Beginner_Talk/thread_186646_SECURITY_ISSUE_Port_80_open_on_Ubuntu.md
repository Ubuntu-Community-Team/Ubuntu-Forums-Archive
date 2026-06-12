---
title: "SECURITY ISSUE: Port 80 open on Ubuntu"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-06-02
Hi all,

I was using angryip to scan for open ports on my network and noticed my ubuntu machine had open port 80... 

so from another host it tried using a web browser to hook onto the ubuntu machine's ip address e.g. 

[http://192.168.200.5](http://192.168.200.5)

then up comes this FTP like folder structure with a title "Index of /"

then theres two icons apache2-default/ and netmrg/

i don't recall installing apache... how do i close this open port for good?

[SIZE="7"]cheers[/SIZE] :mrgreen:

---

### Post by Breuls on 2006-06-02
Try uninstalling apache. It's installed by default and started on each boot.

```
sudo apt-get remove apache2
```

---

### Post by ProjectGod on 2006-06-02
[COLOR="DarkRed"]i tried that but it said i didn't have it installed. i think the problem lies in what i installed earlier... i used apt to install netmgr which has apache, php, mysql dependencies ... basically when i removed NETMRG with apt-get remove --purge i guess the dependencies were left behind and somehow became corrupted... 

DAMN! :mrgreen: talke about "dependency hell"[/COLOR]

---

