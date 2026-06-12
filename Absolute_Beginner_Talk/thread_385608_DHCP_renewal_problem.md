---
title: "DHCP renewal problem"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by tiris on 2007-03-15
I have my Ubuntu Linux box at work and am having trouble with the dhcp stuff. I have actually had it up for quite some time now with no problems but just ran into a problem.

Recently the DHCP server here at work assigned my Linux box an address that another computer was using (it is my suspition that the computer has declared a static IP in the range of the DHCP addresses). I don't have control over the DHCP server configuration.

I wanted to get a different address from the server and tried the following commands but none of them changed the IP that my computer used.

```
sudo /etc/init.d/networking restart
sudo ifconfig eth0 up
sudo ifconfig eth0 down
```

How do I get my computer to get a different IP from the DHCP or even better avoid this IP when requesting an IP?

Thanks

---

### Post by lloyd_b on 2007-03-16
You can try this:
```
sudo /etc/init.d/networking stop
sudo mv /etc/dhcp3/dhclient.leases /etc/dhcp3/leases.bak
sudo /etc/init.d/networking start
```

If you've got a valid lease in "dhclient.leases", then on startup you system will try to reuse that lease.  By moving the leases file, it should force your system to request a new lease, which will hopefully have a different IP (no guarantee on that, however).

The real fix here is to complain to the system admin (if there is one) about that machine with the static IP.  The fact that you're encountering this situation means that either somebody isn't playing by the rules, or the DHCP server is misconfigured.  Either way, it's an admin issue.

Lloyd B.

---

