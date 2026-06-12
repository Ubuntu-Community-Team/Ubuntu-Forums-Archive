---
title: "Block All Traffic"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ubz on 2007-06-03
Hi, I'm looking for terminal command(s) to block ALL inbound and outbound traffic from/to this machine. I would also need the command to revert back to the default mode. I'm using the default Feisty desktop installation with wired nat router cable connection.  I believe Firestarter has this capability but I'm interested to know if this is doable from terminal preferably with a single command line.

Thanks.

---

### Post by HereInOz on 2007-06-03
open a terminal and enter:

man ifdown

This should give you all the information that you need.

---

### Post by oilchangeguy on 2007-06-03
> **ubz said:**
> Hi, I'm looking for terminal command(s) to block ALL inbound and outbound traffic from/to this machine. I would also need the command to revert back to the default mode. I'm using the default Feisty desktop installation with wired nat router cable connection.  I believe Firestarter has this capability but I'm interested to know if this is doable from terminal preferably with a single command line.

Thanks.

wouldn't it be simpler just to unplug the cable going into the machine, when you don't need internet access?

---

### Post by Golyadkin on 2007-06-03
i always use "sudo /etc/init.d/network stop"

---

### Post by ubz on 2007-06-03
> **oilchangeguy said:**
> wouldn't it be simpler just to unplug the cable going into the machine, when you don't need internet access?

I can disconnect this machine from all network access using the Network Management applet but I'd like to try a command line approach to block inbound/outbound traffic.  I'm often away from the computer and would like a quick way to accomplish this without unplugging a wire and prefer not to disconnect via Network Manager as it takes some time to re-estabish connectivity.  Thanks for you suggestion though.

---

### Post by ubz on 2007-06-03
> **Golyadkin said:**
> i always use "sudo /etc/init.d/network stop"

Hi, am I correct to assume "sudo /etc/init.d/network start" puts the machine back online?
thanks

---

