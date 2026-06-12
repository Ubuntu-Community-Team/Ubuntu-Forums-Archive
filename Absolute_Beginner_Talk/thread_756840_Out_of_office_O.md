---
title: "Out of office :O"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-04-16
Hi,
Wondering if anyone knows how to create a server side 'out of office' automated reply for an inbox? Using thunderbird and IMAP, there must be another way right? ^^
Thanks for considering !
:confused:

---

### Post by hyper_ch on 2008-04-16
does procmail do the local delivery on the server?

---

### Post by hungryOrb on 2008-04-16
ehm.. I don't understand a lot about this, but I think we use dovecot IMAP client!

thanks for reply ;]

---

### Post by hyper_ch on 2008-04-16
no, how will the mail server put the messages into the according maildirs?

dovecot is an IMAP server and not a mail server.

---

### Post by hungryOrb on 2008-04-16
Hyper, thanks for replies, I'm going to do a little research first ;]

---

### Post by hungryOrb on 2008-04-16
Seems Exim is the mail handler. Because it's on unix, it's going to have to be done in the unix terminal right?

---

### Post by hyper_ch on 2008-04-16
well, common setups I see is that postfix decides what email is being accepted but then the delivery on the server is done with procmail.... if that is the case for you also, that actually procmail does put the mails into the according maildirs, then you could write a simple procmail recipe :)

However I've never had to do with exim... so I don't know.

---

### Post by hungryOrb on 2008-04-17
Thanks for reply :]

---

