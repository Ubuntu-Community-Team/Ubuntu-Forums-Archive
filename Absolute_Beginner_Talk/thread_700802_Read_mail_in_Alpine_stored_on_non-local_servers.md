---
title: "Read mail in Alpine stored on non-local servers"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Marius1976 on 2008-02-18
Hi!

This is what I want:

I want to be able to read my e-mail that is stored on my ISP's mailserver, using Pine or another console mail client.

I was able to configure alpine to make it possible to sent an email from the console, but what do i have to setup to get my mails into the inbox of pine.

Thanks for your help!
Marius

p.s. it is ok for me if the Linux computer downloads the mails from the ISP mail server first, but they shouldn't be deleted from the ISP's mail server.

---

### Post by mali2297 on 2008-02-24
Check if the mailserver support IMAP or POP (or both).  

I have the following setting in the configuration file ~/.pinerc:
```

inbox-path={imap.myimapserver.se/user=mali2297}INBOX

```
If I instead want to connect to a POP server, the line would look like
```

inbox-path={pop.mypopserver.se/user=mali2297}INBOX

```
View hidden files to find the .pinerc file. This setting can also be done within Al/pine in the menu *Setup > Config*.

---

### Post by metroside on 2008-03-09
Not sure if anyone can help me on this one, but my mail server settings are mail.servername.com for both POP and IMAP. 

As it don't start with POP or IMAP how do you specify in Pine / Alpine which protocol you want to use when filling out the Inbox Path?

Please let me know if there are any work arounds.

---

### Post by mali2297 on 2008-03-09
> **metroside said:**
> Not sure if anyone can help me on this one, but my mail server settings are mail.servername.com for both POP and IMAP. 

As it don't start with POP or IMAP how do you specify in Pine / Alpine which protocol you want to use when filling out the Inbox Path?

Please let me know if there are any work arounds.

I think imap4 is used by default. If you want to use pop3 instead,
```

inbox-path={mail.servername.com/pop3/user=metroside}INBOX

```

---

