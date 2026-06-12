---
title: "Firestarter outbound traffic set at permissive but blocked anyway"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2006-08-29
I have a problem with Firestarter, most probably because I do not understand its concept. Coming from Windows a Firewall is directed at INBOUND traffic. It blocks suspicious traffic, warns you so that you can fully blcok certain IPs etc. It does, as far as my experience, NOT affect outbound traffic.

I installed firestarter checked the settings and for outbound they are set at permissive. I can go to internet, even upload some data but I cannot use Samba: hence I need to switch off Firestarter in order to print or collect data from our central Windows machine.
I tried to allow print traffic via port 631 and IP 127.0.0.1 but nothing happens.

Why does a firewall block outbound (Trojans??)
How do I arrange my Samba connections?

---

### Post by moore.bryan on 2006-08-29
*firestarter is just the gui for iptables, the built-in firewall with linux.  many forum users will tell you you don't need a gui, but i've found it difficult to set-up permissions using just iptable references.  samba requires some different settings which i don't have, but you should be able to find easily by searching the forums.  other users will suggest other gui's (firehol, etc.) and it all comes down to personal preference.*

---

