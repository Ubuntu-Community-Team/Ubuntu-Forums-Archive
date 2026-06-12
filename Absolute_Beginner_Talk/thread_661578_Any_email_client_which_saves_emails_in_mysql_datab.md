---
title: "Any email client which saves emails in mysql database?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2008-01-08
Any email client which saves emails in mysql database?

---

### Post by hyper_ch on 2008-01-08
not that I know of.. why do you want to save it in mysql?

---

### Post by Guruprasad on 2008-01-09
Almost 20 staff  of my office uses a single email id for interaction. We can not have separate ids for everyone due to the organizations structure.

Currently we are using thunderbird over network where the same email files are shared by many users. But it is creating problems for the software.

So I thought a sotware saving emails in mysql database will be easy to access by all users.

If any other solution you have please let me know.

---

### Post by hyper_ch on 2008-01-09
use IMAP instead of POP3

---

### Post by Guruprasad on 2008-01-09
In case of IMAP the emails stays on the mail server itself, isnt it? Most of our emails have heavy attachments which will make it very slow to download everytime.

---

### Post by hyper_ch on 2008-01-09
well, they "also" stay on the server.

In Kontact/KMal you have to select "disconnected IMAP"
In Thunderbird it's just plain "imap"
Dunno about evolution.

This will sync all the mails and hence also download the attachements onto each computer.

---

