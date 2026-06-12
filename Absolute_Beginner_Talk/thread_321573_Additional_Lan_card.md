---
title: "Additional Lan card"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Ameer on 2006-12-19
Hi all

I am trying to install additional Lan card,,,ubuntu is not detecting the card..Plz help me some tips and commands that can solve my problem.

Ameer

---

### Post by szf on 2006-12-19
Have you tried:

```

$ lspci | grep Eth
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

```

---

