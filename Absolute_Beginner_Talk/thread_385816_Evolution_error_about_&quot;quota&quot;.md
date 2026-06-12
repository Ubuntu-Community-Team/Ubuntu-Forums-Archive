---
title: "Evolution error about &quot;quota&quot;"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by misawa on 2007-03-16
I'm using Edgy with Evolution connected to an MS Exchange server.  Yesterday, I started receiving the following error message when sending an email:  > Error while performing operation.

Could not send message.
This might mean that your account is over quota.
It *does* actually send the message, though.  If I boot in to Xp and use Outlook, I get nothing mentioning a quota problem.  So I'm a bit :confused:

---

### Post by deuchar1 on 2007-03-20
Try a purge of deleted messages or something? Maybe you have a backlog of history stored on your Linux disc? Just a suggestion - probably no use at all :confused:

---

### Post by hotani on 2007-04-27
Same here, just started doing it. Any fixes?

This is the exact error:
> 
**Error while performing operation.**

Could not send message.
This might mean that your account is over quota.

Could not send message.
This might mean that your account is over quota.


---

### Post by hotani on 2007-05-04
I fixed this by re-creating my exchange account and deleting the old one.

---

### Post by huhubaer on 2007-07-24
> **deuchar1 said:**
> Try a purge of deleted messages or something? Maybe you have a backlog of history stored on your Linux disc? Just a suggestion - probably no use at all :confused:

I also had this problem.
After deleting the mails from the "Deleted Objects" folder on the exchange server and after a eclipse restart it worked.
I thing evolution is saving the sent mails in the "outgoing" folder on the server, and if you acount is full, ..... :-(

---

### Post by aitorcalero on 2007-08-21
Here you will find the solution:

[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199)

You only need to delete your exchange account in the ~/.evolution/mail/exchange folder

---

