---
title: "What is Multicast DNS service discovery?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2008-01-26
Under: System-->Administration-->Services, one of the options is Multicast DNS Service Discovery. What is it and can I safely turn it off?  When I un-check it, a warning appears that " turning off avahi-daemon may result in data loss."
   Thanks

---

### Post by PeterJS on 2008-01-26
What avahi does is manage adhoc advertisement of services on the network. Apple uses it extensively with their products, it's what iTunes and iChat use to advertise themselves on the network. In ubuntu it's used extensively in extending dbus services over the network. It's also used by pidgin and empathy to implement the Bonjour chat protocol that iChat uses.

If you don't use bonjour, or have apple systems on your network, or other ubuntu systems using network services that you didn't explicitly configure, you can safely turn avahi off. It's pretty cool if you're using it, and pretty useless otherwise.

---

### Post by Stunt Double on 2008-01-26
Thanks for the help.

---

