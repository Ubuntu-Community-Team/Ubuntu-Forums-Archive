---
title: "Evolution filtering on incoming mail not working"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by bforney on 2008-04-17
Hi,

I'm a new Ubuntu user but an old hat Evolution user. When I moved to Ubuntu for my new job, I set up Evolution in a similar fashion as in my old job:

- A default account using IMAP and SMTP with filtering enabled for all new messages in the INBOX a la Preferences > Mail Accounts > IMAP account name > Receiving Options > Apply filters to new messages in INBOX on this server.

- A non-default account using the Exchange connector, which is used for Calendaring, Tasks, and address book lookups but not email. (I've found that the Exchange Connector, while very nice, isn't as reliable for large mail folders as IMAP.)

- A incoming mail filter that if Size > 0, then Copy to Folder "On This Computer/Received mail." This filter should copy all incoming email to the Received mail folder found locally on my computer, making the Received mail folder an archive of all my mail.

Unfortunately, this solution in my new setup with Ubuntu only works sporadically. Any idea why this is not working?

---

### Post by LowSky on 2008-04-17
you actually need to install spam assasin from synaptic, or switch to thunderbird that works right from the start

---

