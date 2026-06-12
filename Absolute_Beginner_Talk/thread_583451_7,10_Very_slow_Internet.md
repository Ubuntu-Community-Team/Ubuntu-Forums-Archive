---
title: "7,10 Very slow Internet"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Don DeGregori on 2007-10-20
Did clean install of 7.10 Final.  Among the many other problems of 7.10, the very slow Internet is the most frustrating. 7.04 Internet is fast, using it right now. Is it the latest Firefox or what? Or the way 7.10 is coded? Some Ubuntu guru please fix ASAP. The new features I would really like to discover, but not be hobbled by slow Firefox.

Thanks, Don

---

### Post by Dr Small on 2007-10-20
What website are you loading that is so slow ?

---

### Post by jayaramk on 2007-10-20
even me too using 7.10 and i don't find it slow... my internet is perfect in everything in both browsing and downloads!!!!

---

### Post by rfruth on 2007-10-20
The default indexing is quite aggressive, I turned it off my old 2.0 MHz P4 couldn't handle it

---

### Post by frank002 on 2007-10-20
type about:config and make network.dns.disableIPv6 TRUE. Someone posted that fix and now Firefox is fine. I still think that if a program worked fine in Feisty, it should work just as good in Gutsy without disabling this or that. Also, this fix did not help with Thunderbird or Evolution. These two programs are still slow.

---

### Post by ddrichardson on 2007-10-20
> **frank002 said:**
> type about:config and make network.dns.disableIPv6 TRUE. Someone posted that fix and now Firefox is fine. I still think that if a program worked fine in Feisty, it should work just as good in Gutsy without disabling this or that. Also, this fix did not help with Thunderbird or Evolution. These two programs are still slow.
That fix will only affect Firefox, if you want to disable IPv6 then do:
```
gksudo gedit /etc/modprobe.d/aliases
```Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.

Reboot Ubuntu

(Straight out of the system help)

---

### Post by Padraig1 on 2007-10-29
My internet is painfully slow too but I don't know how to implement the suggestion above, ie:

[COLOR="Blue"]type about:config and make network.dns.disableIPv6 TRUE[/COLOR]

how do I do this, typing "about:config" in terminal returns "command not found".

Remember, it's easy when you know how!

---

### Post by ddrichardson on 2007-10-29
That command disable IPv6 in Firefox not in Ubuntu, so you type it in the Firefox address bar. If you want to disable IPv6, try my method above.

---

### Post by LowSky on 2007-10-29
type 
about:config 
in firefox address  bar not terminal

---

### Post by Padraig1 on 2007-10-29
thanks for that,
Internet speed is back to normal now.

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

