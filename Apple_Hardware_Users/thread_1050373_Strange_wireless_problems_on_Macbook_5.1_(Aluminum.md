---
title: "Strange wireless problems on Macbook 5.1 (Aluminum)"
date: 2009-01-25
forum: Apple Hardware Users
---

### Post by copyrights on 2009-01-25
hi,

I'm running Ubuntu 8.10 64 bit (Intrepid Ibex) on my Macbook 5.1 (Aluminum). Everything works pretty good by now, but I still got some issues on using wlan. I'm using Netzwerk-Manager-Applet 0.7.0.

I can connect to wireless networks using following encryptions (tested):

WEP, WPA2 personal, no encryption

but I can't connect to:

WPA enterprise, WPA personal

Another strange thing is that all of them work out-of-the-box on my old laptop (ipw2200) running Ubuntu 8.04.1

---

### Post by skigzz on 2009-02-26
I am having the same problem. Unfortunately I have nothing constructive to offer other than helping to confirm that this another issue that needs to be dealt with. I have not seen any of forums where this has been discussed.

---

### Post by Mulien on 2009-03-17
Hi,

I have exactly the same problem. I can use wireless network with following security encryption :
[LIST]
[*]None
[*]WEP 128 bits
[*]WPA2 Personnal
[/LIST]

But when I'm at work, the encryption is WPA/WPA2 enterprise using PEAP authentication (version 0), with a certificate provided by my administrator. Internal Authentication is MSCHAPv.

I have a MB 5,1 and I use Ubuntu 8.10 (Intreprid).

When I try to connect, my laptop just freeze and nothing responds (neither my mouse or keyboard).

I don't have any solution because I'm new on Linux, but I'm interested if someone has an answer.

Thanks.

---

### Post by ago on 2009-05-16
I suspect there is a problem with routers that use TKIP for group policy, while Ubuntu insists in using AES.

---

