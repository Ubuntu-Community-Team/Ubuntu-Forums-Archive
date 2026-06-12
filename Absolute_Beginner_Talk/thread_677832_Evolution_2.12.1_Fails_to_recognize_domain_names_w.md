---
title: "Evolution 2.12.1 Fails to recognize domain names with international characters"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-01-25
Hello Ubuntero's!

Recently Godaddy.com has been selling domain names that may now include international characters like ö or ó or ä etc... etc.... At the moment, domains are only available for .com and .net.

If an email is composed in the Godaddy.com webmail portal characters like “ ö ” which may be in the domain name will be sent without any issue as the Godaddy servers understand how to convert the “ ö “ to a format understood by the mail system.

However, clients like Evolution 2.12.1 or OUTLOOK fail to send e-mail if the address includes a foreign character like ö or ä. Example: [email]name@dömain.com[/email]

I spend the good part of the morning with tech support at Godaddy and they insist that I need to adjust settings within Evolution and Outlook in order to send email to domains with foreign characters.

Does anyone know if this is possible? If so, how is it done? What settings need to be changed. If this is something new and Evolution cannot handle it today how soon will it be before a “PATCH” is created.

Any insight would be appreciated.

Thank you

---

### Post by dcstar on 2008-01-25
> **suomalainen said:**
> Hello Ubuntero's!

Recently Godaddy.com has been selling domain names that may now include international characters like ö or ó or ä etc... etc.... At the moment, domains are only available for .com and .net.

If an email is composed in the Godaddy.com webmail portal characters like “ ö ” which may be in the domain name will be sent without any issue as the Godaddy servers understand how to convert the “ ö “ to a format understood by the mail system.

However, clients like Evolution 2.12.1 or OUTLOOK fail to send e-mail if the address includes a foreign character like ö or ä. Example: [email]name@dömain.com[/email]

I spend the good part of the morning with tech support at Godaddy and they insist that I need to adjust settings within Evolution and Outlook in order to send email to domains with foreign characters.

Does anyone know if this is possible? If so, how is it done? What settings need to be changed. If this is something new and Evolution cannot handle it today how soon will it be before a “PATCH” is created.

Any insight would be appreciated.

Thank you

Try Edit-Preferences-Mail Preferences-Default character encoding.

---

### Post by suomalainen on 2008-01-28
David,

Thanks for the advice. I can't find "Finnish or Swedish" here. Is it possible to add? if so how?

Tried all the other european selections to no avail...

Regards

---

### Post by dcstar on 2008-01-28
> **suomalainen said:**
> David,

Thanks for the advice. I can't find "Finnish or Swedish" here. Is it possible to add? if so how?

Tried all the other european selections to no avail...

Regards

Don't know, you way want to use the Evolution Bug reporting tool to report your issue.

---

### Post by suomalainen on 2008-02-06
Hello Ubunteros,

I thought to ask again if anyone knows how to get the Evolution mail client to convert the "ö" character when it is used as part of the email address.

As everyone probably already knows symbols like ö, ä and á can now be registered as part of the domain name. The issue at the moment is that the main client needs to be configured so it understands how to convert these symbols when used in sending email.

Does anyone know how to do this?

Thanks!

---

### Post by Golem XIV on 2008-02-06
It may be worth a try to use the hex code of the character preceded by a "%", like they use in HTTP URLs (i.e. %20 for space).

The ASCII code for ö is 148, which is hex 94, so use %94

Good luck!

---

### Post by suomalainen on 2008-02-06
Golem XIV thanks again for the input!

I want to be able to achieve using solely the " Ö " character when writing email addresses. Now that international characters can be used as part of the domain name this will need to become a standard feature sooner or later in all worldwide email clients.

Thanks again!

---

### Post by suomalainen on 2008-02-06
Hello Ubunteros!

I really would like to get this working. Does anyone know how to configue Evolution so that it can convert international characters so email can be sent ..


Thanks!!!

---

### Post by suomalainen on 2008-02-09
Hello Ubunteros!

I really would like to get this working. Does anyone know how to configue Evolution so that it can convert international characters so email can be sent ..


Thanks!!!

---

