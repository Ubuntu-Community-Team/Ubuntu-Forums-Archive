---
title: "Email servers"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-06-16
hi,
I'll put this in beginners talk, because i think i'm missing something fundamental.

for years I have setup a mail server for work called Proxy+ on Windows. works great but lacks facilities for us now.
It collects pop3 mail from our Domain hosting provider in one 'catchall' mailbox  (where [email]everyone@mydomain.com[/email] is in one mailbox) every 10 minutes with our broadband connection and uses rules to sort to each users inbox, where they use a client to collect their own mail (eg [email]fred@mydomain.com[/email], goes to freds mailbox etc.).
When we send a message, it goes to a joint 'outbox?' on the internal server and in the same 10 minues check it send mail via our ISP's server for us. POP3 for collection, SMTP for sending.

Most linux mail servers use SMTP for receiving and thats fine, I think I can handle that.
It needs to be a simple product for me to setup. So I looked at several integrated products (don't even suggest postfix or similar with lots of other bits needed) including Axigen pay for product, Hula, Zimbra etc.

But I struggle to see this replication of Proxy+ above of one connection in/out to my ISP and internal sorting by the product . Does every user have to have a seperate mailbox on the internet? Unless i'm wrong, these type of products connect to a seperate box on the net for each user, download mail internally and store it on our server centrally.

Perhaps most of these products expect the server to be exposed to the internet directly and get out DNS record pointed straight to it.
However I would prefer to use it as described above with Proxy + examlpe.


wow!
Jeff

---

### Post by DougC on 2006-06-16
Have a look at this:

[http://www.gentoo.org/doc/en/guide-to-mutt.xml](http://www.gentoo.org/doc/en/guide-to-mutt.xml)

It may give you a few ideas (or maybe not).

It's not ubuntu documentation though.

---

### Post by jethro10 on 2006-06-16
[QUOTE=DougC]Have a look at this:

[http://www.gentoo.org/doc/en/guide-to-mutt.xml](http://www.gentoo.org/doc/en/guide-to-mutt.xml)

It may give you a few ideas (or maybe not).

It's not ubuntu documentation though.[/QUOTE]

thanks, i'll have a look
also found "Popweasle" for windows that I could put on a server that will pick up pop mail and effectivley SMTP it to our internal server, saving putting our server out to the net-safer.
Aslo my conceptual problem with internal distribution rules seems to be with most of these servers that - if it dont exist as an account, its bounced.

I'm getting there.

Jeff

---

### Post by jethro10 on 2006-06-16
CLOSED

Thanks for your help.

solved!

Jeff

---

