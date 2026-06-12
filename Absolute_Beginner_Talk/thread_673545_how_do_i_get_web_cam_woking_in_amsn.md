---
title: "how do i get web cam woking in amsn"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-01-20
i have a web caqm and i wanna se it with amsn

---

### Post by spiderbatdad on 2008-01-20
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN)

---

### Post by Kedster on 2008-01-20
how do i do that
[PHP]You are firewalled or behind a router

If you are unable to view a webcam in aMSN after a contact has send you an invite, or after you have issued the command to receive/send webcam, and you are behind a router, you may need to follow these steps:

If you receive: IP-Restrict-NAT and you receive false in webcam wizard, that means your connection is firewalled. (does not send the IP)

If this is the case, you will need to open some ports for the webcam to use because they are currently blocked.

To do this, open your router web-based configuration (check router manual for details on this). Once you have the web-based configuration open, browse for a setting called "port forwarding" or "port range forwarding" or something similar to that. (This might be found under the advanced features for your router).

Now that you have the port forwarding page open, you will want to set the port forwarding range so that aMSN will be able to accept and send the webcam stream.
Here's an example of how you will set up your port forwarding:

Application: aMSN
Start: 6890
End: 6900
Protocol: Both(TCP & UDP)
IP: xxx.xxx.x.xxx
Enabled: X (Yes/True)

Note: xxx.xxx.x.xxx is the IP of your machine that you are trying to send / receive webcam


If you have a web server open on your port 80, you can try to disable it too, sometimes it helps.

General port instructions for Apple Airport Base Station or Airport Express (of course, use ports 6891 to 6900 in the configurations)
http://www.blueskyis.com/bittorrent/airportforwarding.php
[/PHP]

---

### Post by Kedster on 2008-01-20
i have a router i just dont no how to do what its sayin

---

### Post by Kedster on 2008-01-20
please
i really need this for 2 reasons if i can get web cam working well have 3 new ubuntu users and i really want webcam lol

---

### Post by Kedster on 2008-01-20
dont now how to do that stuff it says to do like were is the config file for it and were do i put that line in and were and were do i get my ip adrees for it

---

### Post by Kedster on 2008-01-21
common please

---

### Post by petegreenhorn on 2008-01-21
have you loaded camorama yet , it's the prog to run your web cam

---

### Post by hyper_ch on 2008-01-21
Does your router have a UPnP (Univerversal Plug'n'Play) option that you can activate?

---

### Post by Kedster on 2008-01-21
sorry guys i dont no answer to eather but i will find out by tues night i woulda tonight but wasent around

---

