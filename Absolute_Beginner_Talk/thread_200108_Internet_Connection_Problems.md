---
title: "Internet Connection Problems"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by jalfordvidman on 2006-06-19
I'm still having troubles connecting to the internet. There are two computers in my house, my parents and mine. Mine isn't connected to the internet, but I'd like to from time to time. My parents use Cable and I have an ethernet cable that I can connect to their modem with. I did this and activated my ethernet card; setting my connection to DHCP. Everything looked like it was working until I actually tried to access the internet. Nada. I'm at a loss as to what's actually going on. I can't apt-get, either, which is the real reason I want an internet connection.

---

### Post by Winblowz on 2006-06-19
DHCP is for use with a wireless router. Are you using a router?

---

### Post by jalfordvidman on 2006-06-19
I thought DHCP was a way for the router/modem to assign IP addresses instead of having a static IP address. But no, I'm not using a router, I'm just unplugging my parents' ethernet cable and plugging mine in.

---

### Post by Winblowz on 2006-06-19
Wait, you're right. I was thinking of DHCP on your local network, but I forgot DHCP is assigned by the ISP. Sorry about that#-o 

Hmmm...I'm not exactly sure what the problem is then. Wait and see what other people say.

---

### Post by carverj on 2006-06-19
I personally use a router so wouldn't know from experience. But you could set a static IP address and give that a go. Make sure it is a class C address.
So enter something like 192.168.1.x
x being a number you choose for the host portion of the address
make sure x is between 2 and 254
such as 192.168.1.7

---

