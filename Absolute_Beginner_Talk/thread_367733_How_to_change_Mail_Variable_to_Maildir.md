---
title: "How to change Mail Variable to Maildir"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-02-22
How do I set the mail variable to default to Maildir instead of /var/mail/user?

I recently installed mutt and modded the Muttrc config file to default to Maildir but I am still getting system messages in /var/mail/admin. I would like to have any message send to admin to show up in the Maildir.

I am running Dapper Drake, Postfix and Courier.

Any help would be most appreciated. Thanks.

---

### Post by Mr. C. on 2007-02-22
home_mailbox = Maildir/

in your postfix/main.cf file and postfix reload.

---

