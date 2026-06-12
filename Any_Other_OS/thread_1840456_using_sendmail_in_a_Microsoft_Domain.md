---
title: "using sendmail in a Microsoft Domain"
date: 2011-09-07
forum: Any Other OS
---

### Post by bl00d666 on 2011-09-07
Hi,
recently i create a script to send mail automatically to certain user at a certain date. the script is working very well with a single user but a soon as i tried to use or mailing list distribution group address it refuse to send the mail.
so what happen is when i use sendmail to send a mail to [email]myuser@mydomain.com[/email] its working pretty well but when i use
[email]mailinglist@mydomain.local[/email] the log end with dsn: user unknown
someone told me that because of the .local address being use by Linux to send a mail locally. so what could i do to be able to send to my [email]mailinglist@mydomain.local[/email] address ?
if you need config file or log just ask.
thanks a lot

---

### Post by bl00d666 on 2011-09-09
Bump!

---

### Post by SeijiSensei on 2011-09-09
You don't need an @domain qualifier if you're sending to a local address.  On the box running sendmail, edit as root /etc/aliases and add your list like this:

```
mymailinglist:     user1@example.com, user2@example2.com, [etc.]
```

If the list is long, put the addresses in a text file, one address per line, then use:

```
mymailinglist:     :include:/path/to/your/listfile
```

When you're finished editing /etc/aliases, run "sudo newaliases" to update sendmail's alias database.

Now you should be able to send a message to "mymailinglist", and it will get redistributed accordingly.  You can test whether this works by using the command:

```
sudo sendmail -bv mymailinglist
```

sendmail should reply with a list of all the addresses it found in the alias.  It will also tell you if they are deliverable, but that's not really a true test.  If user@example.com has deleted her account, but example.com is a valid domain with an MX record, sendmail will report that the message is deliverable.  It doesn't check for whether the enduser account actually exists.

Running this command is always a good idea with a new list since it will flag any typos you might have made.

---

### Post by haqking on 2011-09-09
> **SeijiSensei said:**
> You don't need an @domain qualifier if you're sending to a local address.  On the box running sendmail, edit as root /etc/aliases and add your list like this:

```
mymailinglist:     user1@example.com, user2@example2.com, [etc.]
```If the list is long, put the addresses in a text file, one address per line, then use:

```
mymailinglist:     :include:/path/to/your/listfile
```When you're finished editing /etc/aliases, run "sudo newaliases" to update sendmail's alias database.

Now you should be able to send a message to "mymailinglist", and it will get redistributed accordingly.  You can test whether this works by using the command:

```
sudo sendmail -bv mymailinglist
```sendmail should reply with a list of all the addresses it found in the alias.  It will also tell you if they are deliverable, but that's not really a true test.  If [email]user@example.com[/email] has deleted her account, but example.com is a valid domain with an MX record, sendmail will report that the message is deliverable.  It doesn't check for whether the enduser account actually exists.

Running this command is always a good idea with a new list since it will flag any typos you might have made.

Dude you are the mail issue Guru on here IMO.

your posts to mail issues are always quality and informed, respect.

cheers

---

### Post by SeijiSensei on 2011-09-09
Thanks, but I generally limit myself to sendmail issues.  I've never spent much time with Postfix, so that restricts my usefulness here.

I've been managing mail for about 15 years now; I've learned a few things along the way!

---

### Post by bl00d666 on 2011-09-12
its a nice way to send an email to a mailing list created in linux. the problem is my mailing list are manage by active directory and i don't want to change my linux mailing list each time i add or remove someone from the exchange mailing list. i really need to be able to send a mail to a @mydomain.local address. if you need more log just say it.

---

### Post by SeijiSensei on 2011-09-12
Sounds like a DNS problem.  Do you have a local DNS server (AD, for instance)?  Does it support the mydomain.local domain?  Does it have an MX record for that domain that points to the Exchange server?  Does the initial "nameserver" record in /etc/resolv.conf point to that DNS server?

Isn't it possible to do this entirely with Exchange?

---

### Post by bl00d666 on 2011-09-13
yes i do have a local dns server (3 dns server to be exact) i have all my mx record for those dns server. yes its support our mydomain.local domain. and yes the nameserver is record in /etc/resolv.conf.

not in exchange 2003 apparently. i found a script that can autosend email with outlook but outlook have a security where its prompt if you accept or not to let another software to send an email from him each time. and i don't want to remove that security since its could be a security breach.

---

### Post by bl00d666 on 2011-09-21
bump!

---

