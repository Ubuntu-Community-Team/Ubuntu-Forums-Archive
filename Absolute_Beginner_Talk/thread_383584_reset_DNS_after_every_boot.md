---
title: "reset DNS after every boot"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by trcmag on 2007-03-13
Every time after I boot the machine I have to select the correct network setting to have access to the internet.

I do this by clicking on 'system' - 'Administration' - 'Networking'
Then I just click in the empty box at the top and my settings come up.  I then check the check mark on the right then close.

Is there a way I can have this be the default, so I don't have to go through all that every time I boot up

---

### Post by carlosfocker on 2007-04-02
```
sudo gedit /etc/network/interfaces
```

Post whats in this file before you configure using the GUI app. This is what Ubuntu will look to to configure your nic.

---

### Post by zvacet on 2007-04-02
system>administration>network settings>highlight your modem>properties>choose your type of connection(dhcp,static) chek upper left box>close>DNS tab>delete address you find there and replace it with your nameservers>close
```
pppoeconf
```

---

