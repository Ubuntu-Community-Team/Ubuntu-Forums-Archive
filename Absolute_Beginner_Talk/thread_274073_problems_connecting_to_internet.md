---
title: "problems connecting to internet"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Donkeyman on 2006-10-09
I've just installed Ubuntu on an old PC I had kicking around. I finaly managed to get it all up and running and I also got it recognise my ethernet card. However it will not let me connect to the internet through firefox or any other program. I can access my router on 192.168.1.1 and I can ping [www.google.com](www.google.com) and I get a response time. What can I be doing wrong?

---

### Post by wieman01 on 2006-10-09
But you have not installed a firewall and possibly blocked port 80, right?

---

### Post by mongooseman1128 on 2006-10-09
I had that same problem. What fixed it for me was disabling IPv6. Do this by opening firefox. In the address bar type "about:config" and when the screen pops up type in IPv6 as the filter. This should bring up one entry. On the far right hand side it will probably say true. double click it so that the true becomes false and your problem should be fixed.

---

### Post by wieman01 on 2006-10-09
> **mongooseman1128 said:**
> I had that same problem. What fixed it for me was disabling IPv6. Do this by opening firefox. In the address bar type "about:config" and when the screen pops up type in IPv6 as the filter. This should bring up one entry. On the far right hand side it will probably say true. double click it so that the true becomes false and your problem should be fixed.
Yes, that's very likely. Disable ipv6 both in Firefox and globally. The forum is full of similar posts beating this dead horse. :-)

---

### Post by Donkeyman on 2006-10-09
> **wieman01 said:**
> But you have not installed a firewall and possibly blocked port 80, right?

I have not changed anything on my router. It is letting My mac on the same network connect to the internet just fine.

---

### Post by Donkeyman on 2006-10-09
> **wieman01 said:**
> Yes, that's very likely. Disable ipv6 both in Firefox and globally. The forum is full of similar posts beating this dead horse. :-)


Thanks a lot guys, will give this a crack post haste

---

### Post by Donkeyman on 2006-10-09
> **Donkeyman said:**
> Thanks a lot guys, will give this a crack post haste


Right, i looked at the ipv6 and it said false. I double clicked it to say true and now it works. Was that what you meant?

---

### Post by wieman01 on 2006-10-09
> **Donkeyman said:**
> Right, i looked at the ipv6 and it said false. I double clicked it to say true and now it works. Was that what you meant?
Yes, that's it. You can also disable ipv6 globally which means you "blacklist" the corresponding Linux module/program. This will improve your system's performance further. Check it out on the forum.

---

### Post by mongooseman1128 on 2006-10-09
oops I mixed up true and false there. Yeah, disabling ipv6 globally works wonders. I don't remember the exact file you edit to do this but it's remarkably easy, just search for something like "blacklist ipv6" or variations of that

---

### Post by Donkeyman on 2006-10-10
Cool, I'll look up now how to disable it globaly. Thanks again guys! That's one newbie isue resolved. 8 to go.

---

### Post by wieman01 on 2006-10-10
> **Donkeyman said:**
> Cool, I'll look up now how to disable it globaly. Thanks again guys! That's one newbie isue resolved. 8 to go.
What's the other 8?

---

