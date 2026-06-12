---
title: "help w/ fetchmail+Gmail"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by markcholden on 2007-03-16
Hi all,

First, apologies if this is the wrong forum. I was unsure of what forum to put it in. I tried posting about this over on LinuxForums.org, but nobody replied, so I thought the people at this friendly forum here might be of more help.

Disclaimer: I'm a relatively new user (about 1 year, switched from Windows), running Edgy. So I'm still learning, and it's quite possible my problem here is something really basic.

So, my end goal is to back up my Gmail using fetchmail. I was backing it up with Thunderbird, but then I saw this [guide at Lifehacker.com]("http://lifehacker.com/software/gmail/geek-to-live--back-up-gmail-with-fetchmail-235207.php") (which is for Windows+Cygwin) and decided to give the CLI+cronjob method a try, adapting the instructions for Linux. Sounds great, except I'm unable to get it to work. Specifically, I can't get fetchmail to connect correctly to Gmail and download my email.

Here are the contents of my .fetchmailrc file (username and password removed):
```
poll pop.gmail.com with proto POP3 and options no dns
user 'me@gmail.com' there with password 'password' is 'mch' here options ssl
```
And then here's what fetchmail says when I run 'fetchmail -vk >> fetch.txt':
```
fetchmail: Not supported
fetchmail: SMTP error: 550 relay not permitted
fetchmail: SMTP listener doesn't like recipient address `mch@localhost'
fetchmail: can't even send to mch!
fetchmail: SMTP error: 550 relay not permitted
fetchmail: SMTP listener doesn't like recipient address `mch@localhost'
fetchmail: can't even send to mch!
```
And before anyone says anything, yes POP is enabled for my Gmail account. Any tips/help much appreciated. Thanks!

---

