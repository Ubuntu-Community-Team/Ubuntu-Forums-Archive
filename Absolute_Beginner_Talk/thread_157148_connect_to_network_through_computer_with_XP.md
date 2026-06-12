---
title: "connect to network through computer with XP"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by joyntkid on 2006-04-08
that title is probably confusing, but i didn't know how to word it.
im a complete ubuntu and linux newbie.
i have a small dell that i loaded ubuntu on, and it is on a KVM switch with my other computer.
my other computer is running XP Pro, and connects to my network through an 802.11g usb adapter.
i currently dont have any extra wireless cards for the ubuntu pc, but i can connect the two with an ethernet cable.
it would be way to hard to connect my ubuntu computer straight to the router, seeing as its far away.

i just need to know how to connect to the internet and network through the ethernet cable going to my other pc. or if there is another way to do it.

thanks.

---

### Post by John.Michael.Kane on 2006-04-08
Are you trying to network with windows, and ubuntu/linux?. If you are you may have to setup samba.

---

### Post by Iain on 2006-04-08
You should be able to tell Windows XP to bridge the two network connections (see [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/hnw_bridge_install.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/hnw_bridge_install.mspx?mfr=true) for more information). Alternatively, if you can't get this to work, you could use Internet Connection Sharing. Remember to use a crossover ethernet cable if it's a direct NIC<->NIC link.

---

### Post by rubrboots on 2006-04-08
I tried the bridge method. And it actually worked, its the first time my ubuntu box has ever seen the internet. BUT... strangely the wireless connection on the xp box claims that is was disconnected even though it must have been working or neither of my computers would have had internet.:-k Is there a way to fix this?

---

### Post by Iain on 2006-04-08
Hmm, that's odd. Can't help you on that one I'm afraid.

---

