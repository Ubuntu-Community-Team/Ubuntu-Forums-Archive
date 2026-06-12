---
title: "postfix help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by hockey97 on 2008-01-06
I have postfix up and running. I have mysql communicating with postfix and a couple databses for domain,mailbox/users and alias which I don't use.

it worked somewhat I can get e-mails but can't send them to wellknown e-mail providers. I also config the user to have the maildir to be in /home/user/domian/user but postfix still send's the main in the default area at /var/mail/user .

I mainly want to know how I can config postfix so that I can make the user and user's e-mail address. and also to using php or mysql to be able to automaticly add new users mailboxes ect.

do I need COURIER IMAP to do this?

I have so far been working on this for a week. and havent gotten anywhere.

the latest thing I am look at is :[http://www.postfixvirtual.net/postfixconf.html#mysql](http://www.postfixvirtual.net/postfixconf.html#mysql)

that's mainly it. I specified in main.cf for postfix the base mail and virtuial mail which in the database holds the maildir for the user yet postfix still send's e-mail to the default area the /var/mail/user.

I really need some kind of advice. I am really struggleing here.

---

### Post by dcstar on 2008-01-06
> **hockey97 said:**
> I have postfix up and running. I have mysql communicating with postfix and a couple databses for domain,mailbox/users and alias which I don't use.

it worked somewhat I can get e-mails but can't send them to wellknown e-mail providers. I also config the user to have the maildir to be in /home/user/domian/user but postfix still send's the main in the default area at /var/mail/user .

I mainly want to know how I can config postfix so that I can make the user and user's e-mail address. and also to using php or mysql to be able to automaticly add new users mailboxes ect.

do I need COURIER IMAP to do this?

I have so far been working on this for a week. and havent gotten anywhere.

the latest thing I am look at is :[http://www.postfixvirtual.net/postfixconf.html#mysql](http://www.postfixvirtual.net/postfixconf.html#mysql)

that's mainly it. I specified in main.cf for postfix the base mail and virtuial mail which in the database holds the maildir for the user yet postfix still send's e-mail to the default area the /var/mail/user.

I really need some kind of advice. I am really struggleing here.

And I assume you are restarting Postfix after each change so it loads the new configuration?

---

### Post by hockey97 on 2008-01-06
yep it is. 

I restarte it everytime I make changes. I am using virtual mapping becuse mainly using mysql to store user's and their mailbox and also the domain and alias. I also have a table for e-mails with the user's e-mail address so I can in php display or show only that one user's e-mail.

but  postfix mainly uses the old maildir  the one /var/mail/user  it would go with mysql. if I monkey with it I might just screw up the config and have nothing working.

so I need to understand mainly about how postfix deals with request's on user's like the e-mail address.


I have worked with it for a week.and in that time I mainly messed up the config and ended up putting back the config I done that works which is what it is at now.

---

