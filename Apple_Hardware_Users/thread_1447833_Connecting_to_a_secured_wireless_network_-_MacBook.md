---
title: "Connecting to a secured wireless network - MacBook Pro 5,5 / Ubuntu 10.04 Beta"
date: 2010-04-05
forum: Apple Hardware Users
---

### Post by robertlay on 2010-04-05
I have a MacBook Pro 5,5 and have installed Ubuntu 10.04 Beta.

I am able to connect to unsecured wireless networks, just not secured networks - particularly mine. I don't get any feedback on why I can't connect - at least that I am aware of. Is there a log file somewhere? Additionally, my wireless network is hidden, but I have set up my wireless network settings in System > Preferences > Network Connections : Wireless. I have also tried connecting to my network by clicking "Connect to Hidden Wireless Network" and still nothing.

Would anyone with experience in this area be willing to provide suggestions - next steps to take?

Thank you!

Robert

---

### Post by linuxopjemac on 2010-04-06
my experience with networkmanager and Ubuntu is bad, I switched to wicd. It might work for you too

```
sudo apt-get install wicd
```

if you want to get back to how it was before:

```
sudo apt-get install networkmanager
```

---

