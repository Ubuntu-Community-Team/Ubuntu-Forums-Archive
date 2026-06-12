---
title: "Imap server that gathers my pop mail"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by doc_holiday on 2008-02-04
I'm looking for a mail server that can gather all my pop mail from different accounts and make them available using imap. What do I need to do this?

---

### Post by jakev383 on 2008-02-04
> **doc_holiday said:**
> I'm looking for a mail server that can gather all my pop mail from different accounts and make them available using imap. What do I need to do this?

fetchmail will grab email from just about anywhere and you can then deliver it locally to whatever email account you wish. From there you would access the new account with IMAP.

---

### Post by doc_holiday on 2008-02-04
> **jakev383 said:**
> fetchmail will grab email from just about anywhere and you can then deliver it locally to whatever email account you wish. From there you would access the new account with IMAP.

What will then happen when I use the reply button? With what address will I be sending?

---

### Post by jakev383 on 2008-02-05
> **doc_holiday said:**
> What will then happen when I use the reply button? With what address will I be sending?

Depends on how you set it up and your mail client. Some clients allow you to receive from an IMAP, but send through an SMTP server in which case you would be sending through whatever account you want.
You can also just change your reply-to address in your client. That would probably be easiest.

---

