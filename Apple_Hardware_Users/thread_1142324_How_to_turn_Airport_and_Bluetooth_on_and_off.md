---
title: "How to turn Airport and Bluetooth on and off"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by olembe on 2009-04-29
Greetings all!

I'm very happily running Kubuntu on a 4,1 Macbook Pro. Just one thing: on battery I'm getting much lower life than when I run Mac OS on the same machine and I guess a big part of that is that I can't work out how to turn off Airport and Bluetooth under (k)ubuntu. Apple have made these entirely software-controlled, without ugly (but useful) hardware switches to turn them on and off. 

Has anybody worked out how to do this? It would be incredibly useful!

---

### Post by anando on 2009-04-29
For bluetooth:

```
sudo /etc/init.d/bluetooth start
```or 
```
sudo /etc/init.d/bluetooth stop
```seems to work for me.

For wireless, right click on the NetworkManager applet and check box 'Enable Wireless'.




> **olembe said:**
> Greetings all!

I'm very happily running Kubuntu on a 4,1 Macbook Pro. Just one thing: on battery I'm getting much lower life than when I run Mac OS on the same machine and I guess a big part of that is that I can't work out how to turn off Airport and Bluetooth under (k)ubuntu. Apple have made these entirely software-controlled, without ugly (but useful) hardware switches to turn them on and off. 

Has anybody worked out how to do this? It would be incredibly useful!

---

