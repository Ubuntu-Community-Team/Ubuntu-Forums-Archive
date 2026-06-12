---
title: "SSH-Not Connecting"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by dwessell on 2006-03-03
Hi all..

I have a desktop running Kubuntu, and a Windows laptop..

I installed Open SSH on the desktop using synaptic.. 

Made sure that it was running in the background..

Setup port forwarding on the router, to send all port 22 request to the desktop.
Made sure that the firewall on the router was allowing port 22 to come in.

Went to the windows machine to connect via F-Secure SSH.. Connection times out though..

I'm attempting to connect using the WAN IP address, since I setup port forwarding, won't this send to the desktop automatically (Three computers behind a router, connected to a cable modem)?

Any thoughts would be welcome.

Thanks
David

---

### Post by anacron on 2006-03-03
try putty instead of f-secure ssh?

also, if you can connect inside NAT then the firewall settings are wrong
so just try to play with those, you could try firmware update also?

---

### Post by dwessell on 2006-03-03
When you say inside the network.. 

Do you mean connecting from inside the network using the WAN IP?

Or connecting inside the network using the IP of the desktop, as defined by the router?

Thanks
David

---

### Post by anacron on 2006-03-06
by inside the network I mean not from wan.
if it works, then it's your router settings which blocks it.

---

