---
title: "What kind of mailserver to choose?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-22
Hello all. We're trying to replace Lotus Inotes (web based email client) with a cheaper alternative. I think a mailserver running on Ubuntu would be great, and I've seen some HOWTO's on the subject but they dosn't really explain the pros and cons on all the alternatives.

I need a mailserver that's easy enough to set up and got the basic features for administration. The client should be web based and easy to use. Dosn't have to have a lot of advanced features but it should look somewhat nice and clean.

It's client user base is mostly middle-aged elementary school teachers that likes it plain and simple, hardly the adventure type.

As I'm pretty new to Linux in general myself, I could use some tips on what mailserver to check out..

Thanks in advance!

---

### Post by el3ktro on 2006-03-22
I've set up a mailserver with Postfix/Courier-IMAP/POP3 and Squirrelmail for web access. Authentication is done via MySQL, so the number of users/mal accounts is virtually unlimited, and it supports multiple virtual domains. All mails are auto-checked for viruses, spam is filtered out on the server-side. I've found the how-to for this on [www.workaround.org](www.workaround.org), the instructions are for Debian, but 99% of them should be the same on Ubuntu.

I'm running this mail server privately for me, my family, a few friends, my father's office for over a year now without any problems ever. I can very much recommend this setup. If you have any questions regarding to it (features, security ...) then just ask!

Tom

---

### Post by alamba on 2006-03-22
I have a similar setup on a debian box with uebimiau webmail instead of squirelmail. I pretty much just made this by readying up on the components of the solution.

A

---

### Post by Nunyah on 2006-03-22
I'm really impressed at how quickly people responds to new threads in this forum! ;)
The package you mention seems really nice. Could you explain how the components work?

The way I see it, I first need to install MySQL, then apt-get Courier which will connect itself to the SQL database and automatically create a contact DB which I can administrate via a web based controlpanel. Then i need to install Squirrel Mail on the server in order to have clients to communicate via the mailserver?

[www.workaround.org](www.workaround.org) seems to be down at the moment so I'll check it out later.

---

### Post by Nunyah on 2006-03-22
Also, does Squirrelmail support norwegian language? This is something i forgot to mention earlier which is kinda crusial for the users..

---

### Post by localzuk on 2006-03-22
[QUOTE=alamba]I have a similar setup on a debian box with uebimiau webmail instead of squirelmail. I pretty much just made this by readying up on the components of the solution.

A[/QUOTE]

Why do you use uebimiau? It is out of date, unsupported (no updates for several years IIRC) and has an annoying 'quota' bug.

I believe neomail is based on uebimiau but is newer and kept up to date? [http://sourceforge.net/projects/neomail/](http://sourceforge.net/projects/neomail/)

HTH - I know it is off topic

---

### Post by el3ktro on 2006-03-22
Hello,
uhm damn workaround.org is indeed down, but wait until they're online, it's a really great step-by-step howto for setting up everything. well you need to install a few things:

courier-pop3
courier-imap
squirrelmail
postfix
mysql
...
...

Basically it works as following:

Postfix is used to SEND emails from YOUR users to other users. Courier-IMAP is used so that YOUR users can read their email. They can use Outlook/Thunderbird whatever to access their mail. Squrirrelmail is for webmailing, but it also needs Courier-IMAP. All user account data (mail address, passwords etc.) are stored in a MySQL database - centrally, for all programs involved. You can either use a webadmin tool for MySQL (like PHPMyAdmin) or you can add the entries to the MySQL database via the command line (this is also pretty easy).

Setting up virus/spamscanning is an optional - but recommended - thing. Once this thing is up and running, when you want to create a new email adress for a new user, it's as simple as adding a new username/password pair into the MySQL table. That's quick & easy.

I'm not sure if Squrrelmail is there in Norwegian, but I think so, perhaps you can check their homepage.

Tom

---

### Post by Nunyah on 2006-03-22
Thanks man, really appreciate your answers! I know the basic syntax in MySQL cmd line and with some HOWTO's I think I'll be fine. I'll check their page for language pack. Kind of sad that some teachers can't settle with something as simple as 'send', 'read', 'reply' and 'attach' but it's the very fact. At least here where I'm at..

---

### Post by Nunyah on 2006-03-22
By looking at the [http://www.squirrelmail.org/about.php](http://www.squirrelmail.org/about.php), there are listed up norwegian translators so I guess its supported. Correct me if I'm wrong..

---

### Post by LKRaider on 2006-03-22
Google has a cache of the workaround.org Postfix how-to:
[http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1](http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1)

---

### Post by el3ktro on 2006-03-22
[QUOTE=LKRaider]Google has a cache of the workaround.org Postfix how-to:
[http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1](http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1)[/QUOTE]

Cool, thanks. Well I can really recommend this guide. It has clear step-by-step instructions, and after each major steps you are given a few tests to see if everythings working. The MySQL commands are not explained in the guide I think, they suppose you use PHPMyAdmin - but if you need help with MySQL then tell me. Adding a new user's mail address is as simple as this:

INSERT INTO users (email,password) VALUES ('user@domain.no','secret');

Tom

---

### Post by Nunyah on 2006-03-22
Yep, looks good. Thanks guys!

Anyone got experience using the norwegian language pack?

---

### Post by und3rtug4 on 2006-05-11
[QUOTE=LKRaider]Google has a cache of the workaround.org Postfix how-to:
[http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1](http://www.google.com/search?q=cache:pVA-3d3M8sAJ:workaround.org/articles/ispmail-sarge/+&hl=en&ct=clnk&cd=1)[/QUOTE]

Nice one.....

This guide is very usefull and compreensive!

Thanks to alll

;) ;) ;)

---

### Post by rklauco on 2006-05-13
I have a problem with the guide.
On my latest install (dapper), there is no amavisd.conf file created.
Can I do something with it?
Thanks  in advance for help...

---

