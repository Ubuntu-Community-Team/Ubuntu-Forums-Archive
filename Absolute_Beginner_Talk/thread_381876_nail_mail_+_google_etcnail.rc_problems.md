---
title: "nail mail + google /etc/nail.rc problems"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by 2501 on 2007-03-11
I was able to send email through Gmail using Nail mail program. But my problems is that I am getting a message saying "Unecpected EOF on Smtp connection...."

This is my /etc/nail.rc:

#google
set smtp-use-starttls
set smpt=smtp.gmail.com
set pop=pop.gmail.com
set from="myusername@gmail (slax2501)"
set smtp-auth-user=myusername
set smtp-auth-password=mypassword

Any idea to resolve this problem?????

Thank you in advcance.

-2501

---

### Post by diatribe on 2007-03-11
set smpt=smtp..gmail.com

I think that should maybe say set smtp

---

### Post by 2501 on 2007-03-11
i checked my Thudermail-gmail configuration and it is setup like that.

set smtp=smtp.gmail.com

any other idea??????? thank you for your quick reply.

-2501

---

