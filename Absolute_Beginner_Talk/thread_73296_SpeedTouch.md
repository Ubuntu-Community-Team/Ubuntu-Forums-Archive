---
title: "SpeedTouch"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by gruszczy on 2005-10-08
Hello!

I tried to configure my modem, using HOWTO from this forum and linux-usb.org HOWTO, but it didn't work. However, when I look in the log I can see:

```


Oct 9 01:07:34 ubuntu kernel: [4295853.102000] ADSL line is synchronising 
Oct 9 01:07:49 ubuntu kernel: [4295868.102000] ADSL line is up (384 Kib/s down | 96 Kib/s up)


```

I try to open some website in mozilla, but it can't be done. I used script from this HOWTO and tried typing in pppd call, but none of these work. While using pppd call I can see in the log, that chap-secrets work fine, dns servers are found, but still, I cannot connect with any website (and there are no othere messages in the log). I also checked, if /etc/resolv.conf has dns serves adresses in order. Everything looks perfectly fine. Also while booting, adsl line is up, but still no website can be reached.

Can anyone help me?

---

