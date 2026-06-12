---
title: "Support for Realtek RTL8139?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Ann_Onnymus on 2007-02-13
Am I the only one having problems with the Realtek RTL8139 LAN card or is there no support for it in the more recent kernels?

Decided to try Ubuntu after scrapping my 'ancient' FC4 distro.  Doesn't see eth0, ifconfig only showing lo.  Drivers list shows 8139 but modprobe still fails to pick up my card.

Is this a bug in the newer kernel and if so where can I get an older kernel from?

Now stuck with Windows (yuk!!) for my internet connection and no e-mail as I refuse to set it up on my Windows side.

Help

---

### Post by Archmage on 2007-02-13
I've got a RT8**0**29 and RT8129 runing in one PC, therefore I guess it is still supported.:)

---

### Post by serlex on 2007-02-17
anyone got solution to this? just installed Dapper, didnt recognize my RTL8139 network card! and I thought my card was popular :(

I have tried ```
 modprobe 8139too
```

still no luck, anyone?

---

### Post by simber on 2007-02-17
i have some realtek 8139 cards in my lan and they are working perfectly

can you post the outcome of : "lspci" from the command line 

am using also dapper

---

### Post by serlex on 2007-02-17
worringly "lspci" outputs nothing :s

---

