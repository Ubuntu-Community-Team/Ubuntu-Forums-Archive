---
title: "Postfix and Mailman not getting along?!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by HedonismBot on 2006-08-17
Quick question regarding Mailman and Postfix...

I get a "recipient not in local table" message from postfix when I try and send a message to my mailman list since we've changed the name of the list from "modle" to "modle-update". We use a server for incoming and one for outgoing. The incoming server is the one returning the error when we try and post a message to our broadcast list.

I'm a n00b here so please bear with me. I've tried making an alias in the postfix virtual file to point to the right server for the software address but nothing works.

Here's the exact message when I grep our server, named gluttony:

Aug 17 17:48:16 gluttony postfix/smtp[45960]: E452B3FA9: to=<modle-update@news.XXXXX.com>, relay=mail.XXXX.com[10.10.10.15], delay=3008, status=deferred (host mail.XXXXX.com[10.10.10.15] said: 450 <modle-update@news.XXXX.com>: Recipient address rejected: User unknown in local recipient table (in reply to RCPT TO command))

How do I point postfix in the right direction? I'm clueless when it comes to mail servers and since our guru is off for the month, I've been left to flop around and try and fix this.

help.

please.

---

