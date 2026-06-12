---
title: "Share internet from Mac?"
date: 2009-08-31
forum: Apple Hardware Users
---

### Post by stair314 on 2009-08-31
The place where I live only has WiFi provided to the neighborhood by a government grant-- no wired connections are available. I have an Ubuntu desktop with no wireless card that I would like to get online. I thought I would be able to do this by using "internet sharing" from a Macbook connected to it by ethernet, but that's not doing anything. Any suggestions for how I can debug it? I am testing the connection by pinging 208.67.219.230 (google) and not getting any reply, so it's not a DNS issue.

---

### Post by Bachstelze on 2009-09-01
> **stair314 said:**
> The place where I live only has WiFi provided to the neighborhood by a government grant-- no wired connections are available. I have an Ubuntu desktop with no wireless card that I would like to get online. I thought I would be able to do this by using "internet sharing" from a Macbook connected to it by ethernet, but that's not doing anything. Any suggestions for how I can debug it? I am testing the connection by pinging 208.67.219.230 (google) and not getting any reply, so it's not a DNS issue.

We need the IP configuration (address and netmask) of both interfaces of your macbook, and of your Ubuntu system. Also, are you using a switch or connecting them with a single cable? In the second case, make sure it is a ["crossover" cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable").

---

### Post by stair314 on 2009-09-15
Thanks for the advice. In the end my apartment building management ran into financial difficulties and shut down the free internet, so I got cable.

---

