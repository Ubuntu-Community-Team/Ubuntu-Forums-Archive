---
title: "console dhcp"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2007-05-10
How can I force an interface to get a dhcp address from command line?  I have a box where the interfaces didn't come up right away. I did a ifconfig eth0 up and it shows up in ifconfig now but without an address.  What command can I do to make it pull down an address dynamically?  Thanks.

---

### Post by Najand on 2007-05-10
Try to restart the network using:
```

sudo /etc/init.d/networking restart

```
It will get a dhcp from the server again.

---

