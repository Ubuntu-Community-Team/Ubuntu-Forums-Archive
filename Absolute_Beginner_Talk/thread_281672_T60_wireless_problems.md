---
title: "T60 wireless problems"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by AnonymousFan9 on 2006-10-21
I just installed Ubuntu 6.06 LTS on my thinkpad T60. So far everything's been working really well, but my wirelesss card is not showing up in the list of network devices, all it shows is "Modem" and "Ethernet". In addition, the wireless light on the outside of my laptop is not lit up, suggesting the my wirless card is not on, but there's no way to turn it on since pressing Fn+F5 does not work in linux. It seems like everyone else using the T60 had the wireless working immediately, does anyone know why my card isn't showing up?

---

### Post by jqk on 2006-10-21
You might need ndiswrapper or madwifi depending, on which one, supports your wireless card. 

If you could tell us, what is the brand and model of your wireless card, we could help you.

---

### Post by AnonymousFan9 on 2006-10-21
ok I have an intel ipw-3945 card. I tried installing the drivers but I have to install IEEE80211 and when I try to do the make command it says:
Bash: make: command not found

---

### Post by bswilson on 2006-10-21
> **AnonymousFan9 said:**
> ok I have an intel ipw-3945 card. I tried installing the drivers but I have to install IEEE80211 and when I try to do the make command it says:
Bash: make: command not found

You're getting close.  You first need to install a set of packages that will allow you to compile code; **make** is included in that package:

```
$ sudo apt-get install build-essential
```

Run the command above, then try to install IEEE80211 again.

---

