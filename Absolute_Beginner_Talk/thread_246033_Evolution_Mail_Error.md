---
title: "Evolution Mail Error"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Gorlist on 2006-08-28
Hi, trying to move over to Evolution mail, if I setup the account and go to Send & Receive it comes up with the following error (though it has managed to download the emails from the account):
[B]
Host lookup Failed: mydomain.co.uk.mail: Name or service not  known [/B]

Done searching on the web, read through the docs but can't find anything related.

Setup as POP/SMTP with hostname off mail.mydomain.co.uk, authentication required. 

Works fine in Thunderbird...

Anyideas?

Regards!


**Update* resolved the issue by forcing email send for some reason?**

---

### Post by jimrz on 2006-08-28
> **Gorlist said:**
> Hi, trying to move over to Evolution mail, if I setup the account and go to Send & Receive it comes up with the following error (though it has managed to download the emails from the account):
[B]
Host lookup Failed: mydomain.co.uk.mail: Name or service not  known [/B]

Done searching on the web, read through the docs but can't find anything related.

Setup as POP/SMTP with hostname off mail.mydomain.co.uk, authentication required. 

Works fine in Thunderbird...

Anyideas?

Regards!


**Update* resolved the issue by forcing email send for some reason?**

Are you sure thi, "mydomain.co.uk.mail" is correct? It looks a little backwards. Although, it sounds like you are getting your incoming mail ok...have you tried "smtp.mydomain.co.uk" for your outgoing setting?

Also might check with your e-mail provider for the correct settings needed

---

### Post by Gorlist on 2006-08-29
Hi, its working fine with no errors since forcing a send email - thats what was confusing on the error message, but its correct - mail.mydomain.co.uk. 

Thanks for the reply,

Regards

---

### Post by clesage on 2006-08-29
I am having a similar problem where I can't seem to communicate to any smtp server. It just times out, regardless of Evolution's settings.

What do you mean by "forcing a send mail"? Can you elaborate so I can try as well?

Thanks,
-sage

---

### Post by Gorlist on 2006-08-30
> **clesage said:**
> I am having a similar problem where I can't seem to communicate to any smtp server. It just times out, regardless of Evolution's settings.

What do you mean by "forcing a send mail"? Can you elaborate so I can try as well?

Thanks,
-sage

Hi Sage, unfortunately mine never timed out, and could still download emails regardless of the error message - I had to go to the Outbox, write and email and hit the Send button on the email its self, once I had done that no issues at all.

Might be worth doing a search on Google.

Sorry,

Regards

---

