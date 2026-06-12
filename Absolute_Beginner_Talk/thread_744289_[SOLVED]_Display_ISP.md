---
title: "[SOLVED] Display ISP?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by deafinmyleft on 2008-04-03
Hi all,
I was wondering if there was a way to display one's ISP, prefereably through UNIX.  Thanks in advance

---

### Post by phyrewall on 2008-04-03
Um... display it where?

---

### Post by PeterJS on 2008-04-03
How about:
```

whois `ifconfig *if_name* | grep "inet addr" | awk '{print $2}' | sed 's/addr://g'` | grep OrgName | sed 's/OrgName:\s*//g'

```

Pull your address from ifconfig, clean it up a bit, pass it to whois, and strip that down to just the OrgName. This is assuming you have a public IP, if you don't obtainting your real address is left to the reader, the whois bit stands.

---

### Post by deafinmyleft on 2008-04-03
> **phyrewall said:**
> Um... display it where?

I would like to display it in a terminal

> **PeterJS said:**
> How about:
```

whois `ifconfig *if_name* | grep "inet addr" | awk '{print $2}' | sed 's/addr://g'` | grep OrgName | sed 's/OrgName:\s*//g'

```


I pasted this into a terminal, but received the following error message:

*if_name*: error fetching interface information: Device not found
Usage: whois [OPTION]... OBJECT...

Any ideas?

---

### Post by PeterJS on 2008-04-03
You need to replace if_name with the name of you public facing network interface.

---

### Post by phyrewall on 2008-04-03
LOL, I get IANA!

```
whois `ifconfig eth0 | grep "inet addr" | awk '{print $2}' | sed 's/addr://g'` | grep OrgName | sed 's/OrgName:\s*//g'
Internet Assigned Numbers Authority 
```

---

### Post by stchman on 2008-04-03
> **deafinmyleft said:**
> Hi all,
I was wondering if there was a way to display one's ISP, prefereably through UNIX.  Thanks in advance

If you go to speedtest.

[http://www.speedtest.net/](http://www.speedtest.net/)

After you run the test they display the ISP.

---

### Post by PeterJS on 2008-04-03
> **PeterJS said:**
>  This is assuming you have a public IP, if you don't obtaining your real address is left to the reader...

> **phyrewall said:**
> LOL, I get IANA!

```
whois `ifconfig eth0 | grep "inet addr" | awk '{print $2}' | sed 's/addr://g'` | grep OrgName | sed 's/OrgName:\s*//g'
Internet Assigned Numbers Authority 
```

Like I said, if you don't have an interface with a public IP, you'll need to find your public IP before you run whois. Running whois on a private address is rather useless as you just learned.

---

### Post by Endwin on 2008-04-03
You can get your external IP from here.

[http://whatismyip.com/](http://whatismyip.com/)

---

### Post by deafinmyleft on 2008-04-03
thanks for all your prompt responses, I figured out how to do it via terminal

---

