---
title: "Sendmail not being delivered"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-04-17
Hi,

I am trying to send emails from a machine. We have opened up the SMTP in Firewalls etc, but emails are not being delivered. I don't know where to start to solve this problem. This is parts from the /var/log/maillog

Apr 17 20:17:47 hcat sendmail[8551]: m3HHHlro008551: from=apache, size=474656, class=0, nrcpts=1, msgid=<727e7cb49ac411cc6379ca151d95a0a0@localhost.localdomain>, relay=apache@localhost
Apr 17 20:17:47 hcat sendmail[8552]: m3HHHl10008552: from=<apache@hcat.netras.lab>, size=474720, class=0, nrcpts=1, msgid=<727e7cb49ac411cc6379ca151d95a0a0@localhost.localdomain>, proto=ESMTP, daemon=MTA, relay=raslinux.training.lan [127.0.0.1]
Apr 17 20:17:47 hcat sendmail[8551]: m3HHHlro008551: to=peter.lauri.ext@nsn.com, ctladdr=apache (48/48), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=504656, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m3HHHl10008552 Message accepted for delivery)

/Peter

---

### Post by Bachstelze on 2008-04-17
> **peterlauri said:**
> 
Apr 17 20:17:47 hcat sendmail[8551]: m3HHHlro008551: from=apache, size=474656, class=0, nrcpts=1, msgid=<727e7cb49ac411cc6379ca151d95a0a0@localhost.localdomain>, relay=apache@localhost
Apr 17 20:17:47 hcat sendmail[8552]: m3HHHl10008552: **from=<apache@hcat.netras.lab>**, size=474720, class=0, nrcpts=1, msgid=<727e7cb49ac411cc6379ca151d95a0a0@localhost.localdomain>, proto=ESMTP, daemon=MTA, relay=raslinux.training.lan [127.0.0.1]
Apr 17 20:17:47 hcat sendmail[8551]: m3HHHlro008551: to=peter.lauri.ext@nsn.com, ctladdr=apache (48/48), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=504656, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m3HHHl10008552 Message accepted for delivery)

I think the part in bold is your problem. Incoming mail servers usually don't accept mail coming from a non-existing domain. You'll have to get a falid domain name to send mail from.

---

