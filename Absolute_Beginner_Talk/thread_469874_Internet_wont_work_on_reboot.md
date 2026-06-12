---
title: "Internet wont work on reboot"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by GnuUser on 2007-06-10
Hey since i installed linux (feisty fawn, 64 bit) everytime I reboot (from linux into either linux or to windows) the ntework isnt recognized and I have to shut off the computer and unplug it for 5 seconds to get my nnetwork connection back up, any one know how to help me? Thanks.

---

### Post by ironfistchamp on 2007-06-13
Do you mean that it won't work in Windows aswell as Linux?

If it is just in Linux does using:

```

sudo ifdown <interface name>
sudo ifup <interface name>

```

Get your connectivity back? An example of the interface name would be eth1. 

HTH

Ironfistchamp

---

