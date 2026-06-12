---
title: "evolution 2.12.1.Unable to send emails to me."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by TMpBG on 2008-02-15
Hi,I have evolution 2.12.1.I think I found bug ,but as new linux user it may not be one...it may look silly but.Ok here what I have: two mail accounts (for short) [email]todor1@gmail.com[/email] and [email]todor2@gmail.com.If[/email] I create contact(my name) in "Contacts" and in E-mail line type [email]todor1@gmail.com[/email], [email]todor2@gmail.com[/email] and some other like [email]todor3@abv.bg[/email], when I try to send email to [email]todor3@abv.bg[/email] I can't.This is error :

> Error while performing operation.

RCPT TO <&#1058;> failed: Bad or missing RCPT domain d4sm5186076fga.2

And email stay in Outbox...after some time I fount that in the line "To:" is not [email]todor3@abv.bg[/email] but To: &#1058;

After deleting My contact in "Contacts" there is no more this error.And "To:" line is "To: [email]todor3@abv.bg[/email]"
I am still learning English so sorry if there is too much mistakes.

Todor

---

### Post by TMpBG on 2008-02-16
Hmm...after some experimenting i found that I am unable to send any emails to to any email address that I have type in "Contacts" with "Full name" wrote in CYRILLIC.When i try to send email error show and email stay in Outbox.And in line "To:" is not email address but the first Cyrillic  letter from the name in contacts.If i change line "Full name" from Cyrillic to Roman alphabet there is no more errors.

---

### Post by TMpBG on 2008-02-20
I think I found what problem is.(I don't think it's Cyrillic related.)When type name in line "To" and auto suggestion show and I press enter there is some space and comma added...and I think from this "extra symbols" error thing is coming.It's not happening every time and I am not sure it's Cyrillic related.

---

