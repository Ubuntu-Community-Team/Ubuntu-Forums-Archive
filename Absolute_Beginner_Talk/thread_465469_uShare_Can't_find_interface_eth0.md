---
title: "uShare: Can't find interface eth0?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by nathanziarek on 2007-06-05
I'm trying to see if uShare + Ubuntu will be a good match for my Xbox 360, but I can't seem to get past this part. 

I believe I have uShare installed properly, but when I try to run ```
sudo ushare -c /home/me/media
``` i get the error **Can't find interface eth0**.

I attempted to set up a "route" using the command ```
sudo route add -net 10.0.0.0 netmask 255.0.0.0 eth0
``` which didnt give me any errors, but also didn't seem to work.

I am running Ubuntu on a MacBook and using wireless.

Any help is greatly appreciated!

Nate

---

### Post by init1 on 2007-06-05
eth0 is for ethernet. Try connecting to a modem or router with an ethernet cord instead of using wireless.

---

### Post by smuikas on 2008-01-21
Hi,

I'm having a similar problem. I set the route thus:
```

sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ath0
```

And then tried to add my ushare thus (from within the dir I wanted to share):

```
sudo ushare -n Marsyus -i ath0 -c ./
```

Which spits out:

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

Which doesn't make sense as it seems like I'm specifying the network interface to use (ath0, my wifi card)

Any thoughts?


EDIT:

I found the solution:

```
sudo nano /etc/ushare.conf
```

and find the line that says:

```
# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0
```

Change this to whatever interface you want it to listen on. For example, my wifi card is ath0. So I've changed it to:

```
USHARE_IFACE=ath0
```

And everything is just peachy.

---

