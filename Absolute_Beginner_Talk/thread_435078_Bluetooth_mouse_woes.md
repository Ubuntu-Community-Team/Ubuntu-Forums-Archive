---
title: "Bluetooth mouse woes"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by estei on 2007-05-06
Hi all

I have a Logitech MX900 mouse that is giving me a bit of problems

First my system:
Dell 9300 Laptop with builtin bluetooth
Mouse MX900
Kubuntu Feisty brand new

I have gotten it to work by pushing the connect button under the bottom and then connecting to it with 

```
hidd --connect "physical address"
```
I enabled and  added the connect statement to /etc/default/bluetooth

After having done this the mouse will work as a reguler scroll mouse, but as soon as I reboot the mouse is no longer connected

I do still recieve information from the mouse though because in my /var/log/syslog I get this line everytime I move the mouse

> kernel: [  130.740000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 47

It is as if my computer forgets that it has a connection running with the mouse whenever I reboot

If I push the connect button under the mouse and use hidd to connect again my mouse work wonderfully again until reboot.

I have been searching hi n' low on the net for this but havent really found just that answer I was looking for

Hope to hear from you guys

Thank you
Rasmus Lauridsen
Denmark

---

### Post by junjan on 2007-05-06
You can check this:
[URL="http://ubuntuforums.org/showthread.php?t=227057"]
 HOWTO: Bluetooth Keyboard and Mouse[/URL]

Maybe it helps...

---

### Post by estei on 2007-05-06
ok will have to look at all this tomorrow again right n ow I feel like Im doing the same over and over again 

I will look at the guide you sent Junjan then thank you :-)

---

