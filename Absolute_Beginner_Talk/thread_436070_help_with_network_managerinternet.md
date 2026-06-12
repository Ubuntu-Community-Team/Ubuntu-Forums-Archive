---
title: "help with network manager/internet"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by T-Bone55 on 2007-05-07
Hello,
I'm new to linux.  I have fiesty installed and was following the threads on the network manager not starting a wired connection by default.  So, on the advice of another post I ran this command:
```
sudo apt-get  remove network-manager
```

but I think this has messed up my system.  I couldn't connect at all after this.  So I tried the following to get back to the original state:
```
sudo apt-get install network-manager
```
but this didn't help.
I am in over my head.  Could someone help me get back to where the network manager runs in the system tray and I can get a wired connection.
Many thanks in advance.

---

### Post by Whiffle on 2007-05-07
What happened after you reinstalled it?  Any error messages?

---

### Post by T-Bone55 on 2007-05-07
no error messages at all.  But after reboot, there was no network manager icon in the sys tray at the top right, and no internet connection when I run Firefox.

---

### Post by zvacet on 2007-05-07
system>administration<network settings>select your modem>properties>select type of connection(dhcp,static)>close>DNS tab>remove addres you find there and replace it with your nameservers>close

```
pppoeconf
```

If you still have problems,just post it here

---

### Post by T-Bone55 on 2007-05-08
thanks for your reply.  In regards to this comment:
"replace it with your nameservers"
how do I find the nameservers?
thanks

---

### Post by T-Bone55 on 2007-05-08
one other comment: when I run
#sudo dhclient#
I then have internet connection until I reboot, then I again have no connection, and no network manager.
Any solution to this?

---

