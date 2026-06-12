---
title: "[SOLVED] Problems with sending mail via squirrel webmail"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2007-07-12
Hello. I have problems sending email via squirrel webmail on my ubuntu + postfix mailserver. Have no problems with reciving mail, but with some addresses I get Undelivered Mail Returned to Sender message in return.

Below is the message I get when I try to send mail from webmail on my ubuntu server :


This is the Postfix program at host dillner.net.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                        The Postfix program

<Privatfortolling@posten.no>: host scan.interpost.no[139.117.101.35] said: 554
    Service unavailable; Client host [62.16.239.157] blocked using
    zen.spamhaus.org; [http://www.spamhaus.org/query/bl?ip=62.16.239.157](http://www.spamhaus.org/query/bl?ip=62.16.239.157) (in
    reply to RCPT TO command)



Is there something wrong on my mailserver setup ?
What can I  do to fix this ?

---

### Post by scxtt on 2007-07-12
afaik, some mailservers will reject mail from domains it doesn't "like" ... i used to us postfix to send emails from my PC to my gmail account - this worked for MONTHS, then i started getting rejects from gmail saying it considered my email spam ... there might be a way around it, but i didn't find it (i added my address i was emailing from to my contact list, etc.) ...

---

### Post by chrisdee on 2007-07-13
Ok thanks for reply.

Anybody else have a solution on how I can solve this problem ?






Reguards
CD

---

### Post by scxtt on 2007-07-13
where is your mail coming from?  meaning, if you emailed me, what would come after the @? ... if i was to do an nslookup on whatever that is, would i get something back?

---

### Post by chrisdee on 2007-07-13
From:   	"Mail Delivery System" <MAILER-DAEMON@dillner.selfip.net

---

### Post by scxtt on 2007-07-13
if some emails you send get through and some don't - chances are the "problem" is on the end of the host you're sending too - and there's not much you can do - aside from contact whoever owns that domain and see what kinda of restrictions they have and if it's possible to get your @<address> added to their "allow through" list ...

---

### Post by chrisdee on 2008-03-11
Hello. Now I get an connection timed out message when I try to
send mail via Squirrl Webmail. If i try to send with Outlook it works
fine.

When I use outlook to send i send via smtp.online.no.
When I send from Squirrel Webmail postfix is used.

Is there any workaround for this problem ?
Below is the message I get from posfix.

Im running Ubuntu 6.06.

---------------------------------------------------------------------
This is the Postfix program at host dillner.net.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                        The Postfix program

<Tony.Caffrey@skatteetaten.no>: connect to
    mx2.test.skatteetaten.no[151.187.194.40]: Connection timed out
-----------------------------------------------------------------------

---

### Post by chrisdee on 2008-03-11
Maby its the same problem as when I got the connection refused message some months ago ?

---

### Post by chrisdee on 2008-03-11
This is frustrating

---

### Post by intel on 2008-03-11
Looks like the problem is in postfix configuration then...

which guide did you follow to setup postfix?

---

### Post by chrisdee on 2008-03-13
I found the solution:)

The problem is that I had a blank relayhost is my /etc/postfix/mail.cf
file. When I set relayhost = smtp.online.no (for Norway) it works!

Obviously many host didnt like my mailserver handling outgoing
mail. Maby this is caused by a invalid certificate setup on my
server ?

I also found another workaround in changing outgoing mail port from
port 25 to another port, but I have not tested this yet.

---

