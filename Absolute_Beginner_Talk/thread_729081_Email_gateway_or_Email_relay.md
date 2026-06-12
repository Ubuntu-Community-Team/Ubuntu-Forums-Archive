---
title: "Email gateway or Email relay?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by dualE5335 on 2008-03-19
I have a few devices on my LAN that can send email notification via SMTP, but my ISP blocks SMTP.

All I'd really like to do is get notifications sent to Gmail.

Is there a solution that would allow me to run a local SMTP server, then relay/foward messages to Gmail using IMAP/POP3 (preferably IMAP)?

The following software comes up frequently:
Citadel
Courier
Postfix
qmail
sendmail
Cyrus
ssmtp

But I'm not sure I can get the IMAP resend/relay from the packages.

Any advice would be greatly appreciated.

---

### Post by Golem XIV on 2008-03-19
It' s a bit strange that your ISP blocks SMTP requests...  How do you send e-mail?  IMAP?  Exchange? They may be blocking SMTP relaying (which they should be), but not standard SMTP mail sending.

When I set up a UPS system where I used to work, I just gave it the SMTP server address, the login and password for the account and it worked with no problems.  There was no need for relaying or forwarding. 

I guess you can even create a gmail account for the device and have it send from that account to you, then filter (as "received from").  Gmail supports IMAP, but it is possible that the device doesn't.

---

### Post by dualE5335 on 2008-03-19
The ISP blocks SMTP that is to anyone other then their SMTP server (pretty standard practice for home ISP service in the US)  [http://ubuntuforums.org/showthread.php?t=517014](http://ubuntuforums.org/showthread.php?t=517014) (post talks about Canada but the idea is the same)

The device (a multi-function printer/fax/scanner) can connect to an SMTP gateway, but does so in the clear, which I'd rather not do (sending user credentials in the clear is poor-form).  The device doesn't support sending mail by IMAP.

Email from home is done with a combination of IMAP/Webmail over TLS/SSL

So to rephrase what I'm looking for:

printer ==SMTP==>*ProductYouRecommend*==IMAP-TLS==>Gmail

---

### Post by Golem XIV on 2008-03-20
Can't think of anything that would do what you want.  Maybe as a workaround you can ask your ISP to set up an e-mail account for your multifunction.  E-mail accounts are very cheap these days, even free (my ISP offers 5 free and I use only 2).  This account would be dedicated only to the machine, so even if the password is revealed, no harm would be done.  You just need to log into that account once a week to get rid of accumulated spam and maybe change passwords every month or so.

---

