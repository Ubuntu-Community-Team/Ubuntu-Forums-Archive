---
title: "Sylpheed-Claws can't send mail"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2007-01-16
So the account set up was simple enough, got my GMail account synced with this client. Going pretty good so far. It's just one thing - I can't send any mail for some reason, even though it has my password and everything.

This is from the log error when I tried to test out sending mail (to myself)

```
* Connecting to SMTP server: smtp.gmail.com ...
[23:03:35] SMTP< 220 mx.google.com ESMTP k2sm6537042ugf
[23:03:35] ESMTP> EHLO (my router stuff)
[23:03:36] ESMTP< 250-mx.google.com at your service, [170.215.93.7]
[23:03:36] ESMTP< 250-SIZE 20971520
[23:03:36] ESMTP< 250-8BITMIME
[23:03:36] ESMTP< 250-AUTH LOGIN PLAIN
[23:03:36] ESMTP< 250 ENHANCEDSTATUSCODES
[23:03:36] ESMTP> MAIL FROM:<szf2001@gmail.com> SIZE=358
[23:03:36] SMTP< 530 5.5.1 Authentication Required k2sm6537042ugf
** error occurred on SMTP session
** Error occurred while sending the message.
```

I'm not sure what to do from here...

---

### Post by colinleroy on 2007-01-30
You have to check "SMTP authentication" in the account preferences' Send tab.

---

