---
title: "email exceed quota"
date: 2013-10-31
forum: Any Other OS
---

### Post by davidtuti2 on 2013-10-31
Hi

I set up smmtp with my gmail account to can send mail outside  my LAN.
The problem that I have is that I exceed the quota normally.
I see these log in mail.log

```
Oct 30 11:06:07 raspberrypi sSMTP[4656]: Sent mail for author@raspberrypi (221 2.0.0 closing connection w10sm13930717wia.4 - gsmtp) uid=1000 username=pi outbytes=1628Oct 30 11:06:12 raspberrypi sSMTP[4659]: Sent mail for author@raspberrypi (221 2.0.0 closing connection e1sm13931836wij.6 - gsmtp) uid=1000 username=pi outbytes=1709
Oct 30 11:06:16 raspberrypi sSMTP[4662]: Sent mail for author@raspberrypi (221 2.0.0 closing connection y20sm13917119wib.0 - gsmtp) uid=1000 username=pi outbytes=1845
Oct 30 11:06:20 raspberrypi sSMTP[4665]: Sent mail for author@raspberrypi (221 2.0.0 closing connection qc10sm9863627wic.9 - gsmtp) uid=1000 username=pi outbytes=1549
Oct 30 11:06:26 raspberrypi sSMTP[4669]: Sent mail for author@raspberrypi (221 2.0.0 closing connection fb4sm13948450wib.8 - gsmtp) uid=1000 username=pi outbytes=2254
Oct 30 11:07:18 raspberrypi sSMTP[4694]: Sent mail for author@raspberrypi (221 2.0.0 closing connection ft19sm13941647wic.5 - gsmtp) uid=1000 username=pi outbytes=2254
Oct 30 11:07:21 raspberrypi sSMTP[4697]: Sent mail for author@raspberrypi (221 2.0.0 closing connection fp10sm9560088wib.2 - gsmtp) uid=1000 username=pi outbytes=1477
Oct 30 11:07:25 raspberrypi sSMTP[4700]: Sent mail for author@raspberrypi (221 2.0.0 closing connection ey4sm14031805wic.11 - gsmtp) uid=1000 username=pi outbytes=2014
Oct 30 11:07:30 raspberrypi sSMTP[4703]: Sent mail for author@raspberrypi (221 2.0.0 closing connection e1sm13940448wij.6 - gsmtp) uid=1000 username=pi outbytes=2118
Oct 30 11:07:33 raspberrypi sSMTP[4706]: Sent mail for author@raspberrypi (221 2.0.0 closing connection dn2sm13922731wid.1 - gsmtp) uid=1000 username=pi outbytes=1909
```

I thing that these mails are causing the problem.
Could you help me please?
Thanks and sorry for my english!

---

### Post by Elfy on 2013-10-31
*Thread moved to **Other OS/Distro Support**.*

---

### Post by spjackson on 2013-10-31
Those messages seem to be success messages. What is it that you want help with?
Is it your gmail storage quota that is exceeded?
Is it the number of messages sent (per day or whatever) that exceeds gmail's ssmtp quota?
Is the problem that you want to know what these emails are and/or to stop them being generated?

---

