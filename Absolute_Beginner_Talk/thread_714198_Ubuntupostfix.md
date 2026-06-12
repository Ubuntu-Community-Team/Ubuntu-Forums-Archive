---
title: "Ubuntu/postfix"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by shagcarpet on 2008-03-03
I have Ubuntu Server 7.10 and Postfix installed.  I would like to use this server to relay my internal email to any outside email address (gmail, hotmail, etc...).  All internal clients will be using Outlook express or a similar client.  So far my success has been limited.  On my first install, I was able to relay messages thru the server to any domain that appeared in the [/etc/postfix/main.cf ~ mydestination = ] parameter.  For various reasons I decided to reinstall the OS. Now I can't get mail to forward thru the server at all, regardless of what I put for that parameter.  My email client returns an error [Server Response: '550 5.1.1 <*email@email.com*>: Recipient address rejected: User unknown in local recipient table'].  Any ideas?
Plus...I would like to configure the server to send to ANY email address...is there some type of wildcard that can be used in that parameter so I don't have to add every possible domain?  For now, I'm not concerned about any security...the server is internal to my corporate network.  Thanks a bunch...

---

