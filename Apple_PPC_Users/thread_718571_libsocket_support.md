---
title: "libsocket support?"
date: 2008-03-08
forum: Apple PPC Users
---

### Post by franklynb on 2008-03-08
I'm trying to compile an application that requires a link to "-lsocket"; which I assume is tdp/udp sockets support.

I've installed  happycoders-libsocket_1.6-1build1_powerpc.deb but there are no libraries that come close, where close is grepping on the string 'soc'. Only the palm conduit socket exists.

Obviously, the socket library is either implemented in a different naming structure <i.e. link to a different library> or bured so deeply in launchpad that I can figure it out.

Any suggestions as to .deb's to load? I'm dpkg'g by hand, as synaptics doesn't "get it"either.

thanks!

---

### Post by franklynb on 2008-03-08
Oh! g4 12" ALUM powerbook running feisty 7.04, if that matters.

--f

---

### Post by franklynb on 2008-03-08
Duh. Buried in the '/usr/lib/happycoders' directory ...

---

