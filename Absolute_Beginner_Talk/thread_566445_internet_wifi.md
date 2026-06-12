---
title: "internet wifi"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by kinglouis101 on 2007-10-03
wifi is not working on my new laptop with my new ubuntu, in windows I can see the connection an choose one but in linux ubuntu I cant even do that I dont see any connection and with out it it is useless to me , I really like ubuntu but .... no internet ..... :-)

kinglouis101

---

### Post by hangthedj on 2007-10-03
Please let us know, what kind of computer it is at least.

also if you open a konsole and type

```

lspci | grep Ethernet

```

and post the output, that would be helpfull as well.

thanks

---

### Post by master_kernel on 2007-10-03
Also, can you post the output of:
```
iwconfig
```

---

### Post by Lambert on 2007-10-03
> **kinglouis101 said:**
> wifi is not working on my new laptop with my new ubuntu, in windows I can see the connection an choose one but in linux ubuntu I cant even do that I dont see any connection and with out it it is useless to me , I really like ubuntu but .... no internet ..... :-)

kinglouis101

Wireless in linux is still weak due to manufactures not releasing drivers for their devices. Not sure what version you installed but here are some options.

1. Each release has improved support, if you installed 7.04 you can wait until 7.10 releases in the next few weeks to try again.
2. The community here can walk you through installing a driver and getting your device to work. It can be something as simple as a 3 minute process or it could take some time and a learning curve.

The very first thing that we need to find out is what kind of wireless card is being used so we can check what driver is needed and if it's installed.

One way to do this is to open an app called terminal and type in the following.

```

sudo lshw

```

You can post the entire output here in the forum (will be lengthy because it shows each piece of hardware on your computer) and someone can find the device and start from there.

With out the exchange on the forum, you can also go to wiki.ubuntu.com and search wifidocs for information on thsi subject and to work your way through.

---

