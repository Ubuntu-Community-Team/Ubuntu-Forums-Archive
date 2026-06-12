---
title: "Postfix with SMTPAUTH"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by bonnevent on 2007-06-24
Hey everybody,

I have just installed Ubuntu 6.10 server with the help of the perfect setup from HowToForge. I would like to use the SMTPAUTH feature, so I can send mail through my mai server from everywhere.

I have followed the howto, but I guess I have done something wrong. I am a newbie in Ubuntu and Linux, but I have looked at the /var/log/mail.log and this shows the following error:

[I]Jun 24 11:57:21 web01 postfix/smtpd[26728]: setting up TLS connection from unknown[10.10.1.57]
Jun 24 11:57:21 web01 postfix/smtpd[26728]: TLS connection established from unknown[10.10.1.57]: TLSv1 with cipher AES128-SHA (128/128 bits)
Jun 24 11:57:21 web01 postfix/smtpd[26728]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jun 24 11:57:21 web01 postfix/smtpd[26728]: warning: SASL authentication failure: Password verification failed
Jun 24 11:57:21 web01 postfix/smtpd[26728]: warning: unknown[10.10.1.57]: SASL PLAIN authentication failed: genericfailure
Jun 24 11:57:21 web01 postfix/smtpd[26728]: lost connection after AUTH from unknown[10.10.1.57]
Jun 24 11:57:21 web01 postfix/smtpd[26728]: disconnect from unknown[10.10.1.57][/I]

I also tried to test the connection with testsaslauth, but this also gives an error, like shown below:

[I]testsaslauthd -u <user> -p <passwd>
connect() : Permission denied[/I]

Does anybody have some idea, where I should look to resolve this problem.

Thanks already

---

