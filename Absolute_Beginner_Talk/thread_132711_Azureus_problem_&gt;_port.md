---
title: "Azureus problem &gt; port?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-18
I'm trying to get Azureus running but when I try testing the default port I get the following:

Testing port 6881 ... NAT Error

What does this mean? Do I need to open up the port or something?

Thanks :)

---

### Post by mr.p on 2006-02-18
Yes, you will have to open a port. What is your internet connection setup? Router?

---

### Post by Clark Nova on 2006-02-18
My internet connection is a direct connection through ethernet to my cable modem, no router etc.

---

### Post by Cesium on 2006-02-18
If you are using a firewall, you may have to open the ports there as well.  For example if you are using Firestarter go:

->Policy tab
->right-click on "allow service" and select "add rule"
->select "bittorrent" under name and it should open the ports for 6881-6889
->click "add" to finish.

Hopefully that will help.  If you have another firewall search around...I'm sure there's instructions.  If you had a router, you would have to open ports on that as well.

---

### Post by Clark Nova on 2006-02-18
[QUOTE=Cesium]If you are using a firewall, you may have to open the ports there as well.  For example if you are using Firestarter go:

->Policy tab
->right-click on "allow service" and select "add rule"
->select "bittorrent" under name and it should open the ports for 6881-6889
->click "add" to finish.

Hopefully that will help.  If you have another firewall search around...I'm sure there's instructions.  If you had a router, you would have to open ports on that as well.[/QUOTE]

Thank you very much!:KS

---

### Post by nalmeth on 2006-02-18
I find that I have to change my NAT continually. Don't use the default 6881. For now, try something in the 58000 range:
TOOLS --> NAT FIREWALL / TEST
after getting an ok from the test, accept the change, and give azureus some time.

---

### Post by Protostar on 2006-02-23
[QUOTE=Cesium]If you are using a firewall, you may have to open the ports there as well.  For example if you are using Firestarter go:

->Policy tab
->right-click on "allow service" and select "add rule"
->select "bittorrent" under name and it should open the ports for 6881-6889
->click "add" to finish.

Hopefully that will help.  If you have another firewall search around...I'm sure there's instructions.  If you had a router, you would have to open ports on that as well.[/QUOTE]

I am having the same problem. I have Azureus set to port 50000, and when I open Firestarter and right click on the Policy tab, all the options are greyed out (as in I don't have access to them). I tried running Firestarter from the command prompt using the sudo command and still the same thing. Does anyone know any solution to this?

---

