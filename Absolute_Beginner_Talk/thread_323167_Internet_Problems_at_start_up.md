---
title: "Internet Problems at start up"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-12-21
Each time i restart my computer into edgy, i dont get internet connection unless i type in "sudo dhclient" in console or i unplug the router for 10 sec and plug it back again.
is there a way to fix this problem](*,) ](*,) ](*,)

---

### Post by dbbolton on 2006-12-21
which dhclient are you using ?

---

### Post by kiyometane on 2006-12-21
what is dhclient by the way?

---

### Post by kiyometane on 2006-12-21
can someone help?

---

### Post by EminNew on 2006-12-21
Did you setup your connection with pppoeconf?

If you did, maybe you should run it again, and this time say "no" when it asks if you want to connect automatically at boot.

I had similar problems and this was the solution.

You can connect manually with "pon dsl-provider", check if you're connected with "plog" and disconnect with "pof".

I have only a vague notion of what dhclient is so I'd be doing you no favor if I tried to explain, being a newbie myself.

---

