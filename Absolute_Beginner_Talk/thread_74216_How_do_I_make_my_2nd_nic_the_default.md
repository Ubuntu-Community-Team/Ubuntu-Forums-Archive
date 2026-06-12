---
title: "How do I make my 2nd nic the default?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by loki99 on 2005-10-11
I have setup a box for a friend, which had a broken onboard nic. So I bought another one, stuck it in and booted up. Ubuntu can see it just fine and under network I'm able to deaktivate eth0 and activate eth1. After running dhcp everything is dandy. 

The problem starts when I reboot. All the settings are gone and I have to redo the whole procedure. :( 

So can someone enlighten me about how to store these settings permanetly?

Thanks in advance!

loki99

---

### Post by brt on 2005-10-11
just edit your /etc/network/interfaces and comment out anything regarding eth0

```
sudo gedit /etc/network/interfaces
```

---

### Post by loki99 on 2005-10-11
Thanks a lot for the fast reply! :) 

loki99!

---

