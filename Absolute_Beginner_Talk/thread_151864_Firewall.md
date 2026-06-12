---
title: "Firewall?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Talruk6 on 2006-03-28
Does Ubuntu come with a built-in firewall?  If not, what does everyone recommend?  Tips on configuration?  

Thanks.

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=Talruk6]Does Ubuntu come with a built-in firewall?  If not, what does everyone recommend?  Tips on configuration?  

Thanks.[/QUOTE]
Yes, Ubuntu has iptables built in. It's a very powerful firewall. I would recommend installing firestarter, to observe your firewall and manage it's policies.

---

### Post by rfruth on 2006-03-28
Ubuntu comes with iptables and firestarter is a great GUI for it (here is some general info)  [https://wiki.ubuntu.com/Firewalls?highlight=%28firewall%29]("https://wiki.ubuntu.com/Firewalls?highlight=%28firewall%29")

---

### Post by RedKnight on 2006-03-28
**You can install firestarter using the following code:**
```
sudo apt-get install firestarter
```

If you get to the point where it trys downloading the tar file "ttf-baekmuk_2.2-1_all" this file no longer appears to be available.

**You can download this file from:**
[http://ftp.debian.org/debian/pool/main/t/ttf-baekmuk/ttf-baekmuk_2.2-1_all.deb]("http://ftp.debian.org/debian/pool/main/t/ttf-baekmuk/ttf-baekmuk_2.2-1_all.deb")

**Download and run this command:**
```
sudo dpkg - ttf-baekmuk_2.2-1_all.deb
```

Then re-run the firestarter install and you shouldn't have any problems.
An icon will appear under - Applications>System Tools>FIrestarter
Stuart

---

### Post by John.Michael.Kane on 2006-03-28
And if you ever feel you want to manually edit iptables
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
[http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html)

---

### Post by IDipSkoalMint on 2006-03-28
For those who want to start Firestarter upon login, check out [this]("http://www.ubuntuforums.org/showthread.php?t=151876") thread. ;)

---

### Post by RedKnight on 2006-03-28
Didn't know that cheers :)

Stuart

---

