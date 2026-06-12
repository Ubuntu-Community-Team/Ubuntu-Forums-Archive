---
title: "[SOLVED] Problem with Thunderbird 2"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-03
I installed Thunderbird 2, and set up a gmail account in it. But it doesnt seem to download the mail from the server. It keeps saying 'There are no new messages on the server' on the status bar at the bottom.

At first, i thought it might be because there were no 'new' = unread messages...so i send out a test email and Thunderbird still doesnt download the emails.

I used the default GMail account setting that T2 provides while adding accounts !!

Funny thing is that I sent the test email thru T2 !!!

---

### Post by digital_k on 2007-05-03
While signed in to your gmail account, go into the POP settings and be sure that pop access is enbabled and also check the box that says download email that has already been retrieved. This will allow anything in your inbox to be redownloaded. :) Also be sure your server settings are correct. More info at the link below.

[http://mail.google.com/support/bin/answer.py?answer=13285]("http://mail.google.com/support/bin/answer.py?answer=13285")

---

### Post by Inxsible on 2007-05-03
yes I have already done this. In fact I did download all my mail into Evolution and everything works fine. 

Its just Thunderbird giving me problems !

I can send mails via Thunderbird, I just cant download them :confused:

---

### Post by Billy McCann on 2007-05-03
My prob is the reverse.  I can't send mail w/ gmail, but I can get them.  Spooky.

---

### Post by explemonk on 2007-05-04
> **Inxsible said:**
> yes I have already done this. In fact I did download all my mail into Evolution and everything works fine. 

Its just Thunderbird giving me problems !

I can send mails via Thunderbird, I just cant download them :confused:

Did you download the Gmail emails with Evolution before trying to do it with Thunderbird?  That might be the problem.  [This link]("http://mail.google.com/support/bin/answer.py?answer=47948&topic=1556") at the Gmail FAQs talks about accessing mail via POP with multiple clients/computers.  I was very annoyed with not being able to get my Gmail in Thunderbird on two different computers until I found that link.

---

### Post by Inxsible on 2007-05-04
> **explemonk said:**
> Did you download the Gmail emails with Evolution before trying to do it with Thunderbird?  That might be the problem.  [This link]("http://mail.google.com/support/bin/answer.py?answer=47948&topic=1556") at the Gmail FAQs talks about accessing mail via POP with multiple clients/computers.  I was very annoyed with not being able to get my Gmail in Thunderbird on two different computers until I found that link.

Yes, I had downloaded all mail earlier in Evolution. That helped me download mails in the last 30 days. But how do I download my older mail ?

---

### Post by explemonk on 2007-05-04
> **Inxsible said:**
> Yes, I had downloaded all mail earlier in Evolution. That helped me download mails in the last 30 days. But how do I download my older mail ?

In your Gmail web account, you can go to Settings -> Fowarding and POP and check the radio button that says "Enable POP for all mail (even mail that's already been downloaded)."  Then Thunderbird will redownload every Gmail email you have.  I think Thunderbird then has a command to delete duplicate emails, but I'm not sure where it is.

---

### Post by BRNRDSDJNG on 2007-05-09
I have a problem with Gmail and Thunderbird 2.
In the accounts you can't set the ports. Gmail requires a Secured Login and further normal non secured transfers. (Does not support secured transfer). 
So even setting the TSL (?) will set the port to standard 25 and 110 instead of 
SMTP 465 and POP 995. Both are linked to the standard settings and cannot be changed.
Also with AOL you require different ports for IMAP.
Evolution won't work at all with these servers.
So how did you manage your accounts?

---

### Post by explemonk on 2007-05-09
> **BRNRDSDJNG said:**
> I have a problem with Gmail and Thunderbird 2.
In the accounts you can't set the ports. Gmail requires a Secured Login and further normal non secured transfers. (Does not support secured transfer). 
So even setting the TSL (?) will set the port to standard 25 and 110 instead of 
SMTP 465 and POP 995. Both are linked to the standard settings and cannot be changed.
Also with AOL you require different ports for IMAP.
Evolution won't work at all with these servers.
So how did you manage your accounts?

When I go to Edit -> Account Settings, under each of my accounts I am able to set the port and other options under Server Settings.

---

