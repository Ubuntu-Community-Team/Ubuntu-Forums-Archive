---
title: "Help with internet"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by vladiny on 2007-10-01
I get a wired network connection, and the modem is working fine. My problem is when I open firefox and I start surfing. I can type in [www.google.com](www.google.com) and it comes up. I try to surf a different page and I get server not found all the time. Do I have to do something with firefox?

---

### Post by hyper_ch on 2007-10-01
Do you have IPv6 disabled?

---

### Post by vladiny on 2007-10-01
Where do i find out if IPv6 is disabled?

---

### Post by hyper_ch on 2007-10-01
You could use the forums' search function --> [http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6)

---

### Post by Arwen on 2007-10-01
Or this troubleshooting guide->[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ip](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ip)

---

### Post by vladiny on 2007-10-01
sorry!!

---

### Post by hyper_ch on 2007-10-01
> **vladiny said:**
> sorry!!

Most people don't use the Search... it's very convenient not to use it and let others do the work...

---

### Post by Jadd on 2007-10-01
People, aren't we here to help newbies? If you're not gonna help, why bother posting? Arwen, that guide's irrelevant 'cause vladiny didn't mention wireless at all.
Sorry, vladiny, I'd actually help you, except I don't know what could be wrong. Try disabling IPv6 as suggested, the link's been given.

---

### Post by Arwen on 2007-10-01
I didn't post it for the wireless but for IPv6 section it has.

---

### Post by vladiny on 2007-10-01
Thank you Jadd.
I do not have a wireless connection, I have an ethernet connection. I disabled the ipv6 as stated, but still no connection. How can I change and save my DNS servername, which I believe it may be the problem?

---

### Post by hyper_ch on 2007-10-01
the nameservers are defined in:
/etc/resolve.conf

You could add, for testing, the OpenDNS ones, just replace the content of the file with that here (or rather comment the existing entries first by adding a "#" as first character in each line):
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

---

### Post by vladiny on 2007-10-01
I have tried everything that everyone has said, and nothing is working for me. I have read the howto's, searched this forum, but everything i try does not work. Can someone please help me get my internet up?

---

