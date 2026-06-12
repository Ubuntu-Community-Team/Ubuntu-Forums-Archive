---
title: "Help with wifi"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-25
When I'm at my house my wifi works just fine. But whenever I'm somewhere else, it doesn't work. So how do I connect to another router?

---

### Post by ubutufan on 2007-12-26
Your /etc/network/interfaces file has registered information about your home connection.
Make a back up and edit it. Make sure that the only available settings are the following

auto lo
iface lo inet loopback

Save it and reboot.

That will clear things for you

---

