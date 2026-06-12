---
title: "Windows 7 firewall exception incoming scope rule for different subnet lan router"
date: 2012-12-17
forum: Any Other OS
---

### Post by sdowney717 on 2012-12-17
This one problem kept my win 7 PC from being able to be pinged and share files from incoming ubuntu PC on another LAN with a different subnet.

I have 2 lans, 2 routers, each using a different range of IP.
One is on 192.168.1.x
Other is on 192.168.200.x

I have a static route to direct packets from forward LAN to the other LAN. Only thing was Windows 7 kept blocking that route UNLESS the firewall for the private network was turned off. Even if you turn on sharing, etc... Windows 7 firewall only allows for the subnet LAN it exists on.

So you have to put in a rule and change the scope
The exception is to add your local lan ip range.
For me it scope exception is 192.168.200.0/24

screenshot and also shows the pings from ubuntu PC on different LAN works.

Click Action, new rule, then custom, keep clicking next till you get to scope. Under Local IP, enter your LAN as I did.
Apply it and it works.

---

