---
title: "Mail relay fron Network computers"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-02-04
Hello. I want to be able to send email from Win98 computers which do not have an internet connection. This has to be done through my Ubuntu machine which has a net connection. How do I do this. I installed PostFix but just not able to understand. I am not worried about receiving mail as that is done on another XP PC with a net connection. I want only the ability to relay emails from Outlook Express of Win98 computers to an outside address through Ubuntu machine.

---

### Post by ruy_lopez on 2008-02-04
Before you start thinking about relaying using postfix, you should try sending mail using postfix. A lot of mail servers (which you'll be sending mail to) will reject mail if it doesn't come from an address with a valid DNS record.

Even setting up a dynamic DNS record with dyndns or noip doesn't help. These only resolve a domain name to an ip address. Mail servers usually require a reverse lookup, resolving ip address to domain name.

You'd be better off sharing the internet connection (firestarter has this option), and configuring Outlook as normal.

---

### Post by jesrani on 2008-02-06
Hi, I have rephrased my requirements and put into a new post, [http://ubuntuforums.org/showthread.php?t=689142&highlight=postfix](http://ubuntuforums.org/showthread.php?t=689142&highlight=postfix)
But not getting any replies. I am not a techie and dont really understand what is DNS. Hence I was looking for detailed instructions on how to do this.
I have done this kind of a thing using MailEnable on XP. It has a very easy to understand GUI but in Postfix I am just not able to understand how to make a new Postoffice, new user, which ports to listen to and setup a smarthost. The webmin module doesnt seem to be able to do all this. Can you please look at that post and see if you can help.

---

