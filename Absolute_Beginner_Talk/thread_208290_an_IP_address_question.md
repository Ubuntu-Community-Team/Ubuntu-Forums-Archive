---
title: "an IP address question"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-03
is it possible to change the IP address while being connected to the internet.

if yes please give me the commands!!

---

### Post by PhilOSparta on 2006-07-03
I guess I would have to ask what IP address are you trying to change?

Your own IP address is assigned to your by your Internet Service Provider.
If it is dynamic, you get one every time you log onto the internet.  In that case, you would probably power down or break your ISP connection and then reconnect.  The ISP would then dynamically issue you a new IP address.

If you have a static IP address it can't be changed by you.

---

### Post by wolfmaniac on 2006-07-03
i have a dynamic ip address. yeah it can be changed by switching off the power but what i need is to know that whether i can change it with me connected to the internet.:oops:

---

### Post by steve.horsley on 2006-07-03
You could try **sudo dhclient eth0** (replace eth0 with your interface name), but it is likely that you will be re-assigned the address you already have.

---

### Post by MaximB on 2006-07-03
it is not possible to get a new ip address without being disconnected and then reconnected...
at least I don't think so (never say never)
but you can try to setup a static IP (at the networking) while you connected.
try it and tell me if it worked...(cuz if so it's a miricle...)
why it shouldn't work ?
there are billions of ppl connected to the internet at this moment and you will need to get an address then currently not being used and that is vailed (like subnet address much your ip , your ISP's address...etc...)

---

### Post by wolfmaniac on 2006-07-03
man i made a search and found that there r ppl who reset their ip addresses juz to fool HOSTING sites like "rapidshare" "megaupload" bla bla

---

