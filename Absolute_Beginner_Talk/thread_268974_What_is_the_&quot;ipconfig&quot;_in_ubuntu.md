---
title: "What is the &quot;ipconfig&quot; in ubuntu?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-01
I need to change my IP. Im used to using the command prompt in windows and doing a IPCONFIG /RELEASE>IPCONFIG /RENEW. How would I go about doing this in ubuntu?

---

### Post by xtra2000 on 2006-10-01
ifconfig

---

### Post by sbergman27 on 2006-10-01
ifconfig is more useful for static ip addresses.  For dhcp assigned addreses, you can:

```

/etc/init.d/networking restart

```

This will shut down the interface and then bring it back up, making a dhcp request to the server.  It will ask for the same ip as it had previously.

If you want to explicitly release the old address, you should be able to:

```

/etc/init.d/networking stop
dhclient -r eth0
/etc/init.d/networking start

```

That *should* work.  I have not tried it.  The -r option to the dhcp client is supposed to explicitly send a release request for the current lease.

-Steve

---

### Post by RudolfMDLT on 2006-10-01
Hi!

Something really cool you might want to try is running dual IP's on one nic! This is something that windows can't do. LOL. I used to need to constantly change my IP because of administrating 2 networks at the same time!

---

