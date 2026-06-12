---
title: "Change Root domain name"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by yo_momma on 2006-04-30
Is there a way that I can change the root default smtp email address.  On my system the outbound mails comes from [email]root@ubuntu.loca[/email]ldomainname , and I would like it to show that it came from root@my_external_domain_name.



I am using postfix as my mail agent.


I have searched high and low but haven't found a way to do this.

Thanks in advance for any help I may receive.

---

### Post by Koybe on 2006-05-01
Edit /etc/mailname file. Changer ubuntu.localdomain with your external domain. I'm not sure everything will be route correctly, it depends on your configuration. But it should be ok.

---

