---
title: "configure dsl modem"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by p_p on 2006-07-14
i have a new pc that i just installed ubuntu 6 on and now i am trying to configure my modem so that i can connect to the internet.  i have an actiontec gt701-wg dsl modem which is currently connected to this pc through usb but i am trying to connect it to the new pc through ethernet.  i ran sudo pppoeconf and it apparently recognizes both ethernet ports but after doing the scans it says "the access concentrator of your provider did not respond".  i unplugged the modem and disconnected it from this pc before trying to set it up with the new one.  i tried this separately with both ethernet ports and no luck.  please help.

---

### Post by p_p on 2006-07-14
i'm still hoping someone can help me with this.

---

### Post by dyingsun on 2006-11-27
Hello, just wondering if this issue has been resolved? I'm having the same trouble, but I don't have the techno-savvy to get through it (I've never used DSL before and still getting used to the logistics of it all...)

Cheers!
DS

---

### Post by 56phil on 2006-11-27
There's no nice way to say it. USB modems stink. Have either of you considered using a LAN adapter instead? Ubuntu makes that approach much easier.

---

### Post by dyingsun on 2006-11-28
Hi Phil, thanks for that reply. My modem (slipstream 4200 bundled with my ISP's package) can also connect via Ethernet...reckon this might be a better option? Its only on USB because I've done the initial setup under XP, which is having a spit at the ethernet. Once I've got the hang of it I'm planning to hook it up with a router so I can share the connection with the old man and have a wireless connection for the notebooks. 

Out of interest, why is an Ethernet connection better than USB? Just trying to learn!

Thanks again mate,
Damien

---

### Post by ReaderRat on 2006-11-28
My DSL worked out-of-the-box, but I have a router, not a modem, connected by Ethernet. See if one of these links applies to you:
**[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=dsl&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=dsl&titlesearch=Titles)**

---

### Post by apral on 2006-11-28
I had a similar problem & the only solution for me was to manually enter the dns & static IP address of my ISP.A freindly phone call was all that was needed.:)

---

