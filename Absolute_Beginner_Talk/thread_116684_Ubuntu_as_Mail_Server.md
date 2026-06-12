---
title: "Ubuntu as Mail Server?"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by kerang2k on 2006-01-13
Hi everybody,
A very good evening.  I would like to address a question to everyone on the topic related above which is "Can I setup a box & then configure it as local mail server on Ubuntu?"  The purpose of it was to reduce and cost cutting measures for my company which the budget does not really allow us to have license for ms-exchange server, lotus notes, etc.

So as I'm asking this question I would hope someone could help me or at least provide me some guide on how to actually setup a box for mail server so that I would be able to read through and follow the steps.  The box will serves for about 100 users in my company and to most of them are majority using Ms-outlook 2002 or some using ms-outlook 2003.

Thank you very much for the time and hope someone could guide me on this :)

---

### Post by nocturn on 2006-01-13
You can do this, no problem

You'll need an SMTP server (Postfix is nice)
An Imap (or POP) server, I like Cyrus for this.
Optionally anti-spam/virus, mailscanner is easy and works well.

---

### Post by kerang2k on 2006-01-13
nocturn,
Thanks for the feedback but how can i go about setting it up?  Meaning to say I go get the package such as Cyrus for POP3 and Postfix for SMTP from Synaptic package there is it?   So sorry but I really need some proper guide.  Thanks :)

---

### Post by frodon on 2006-01-13
Is it what you're looking for ? : [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by kerang2k on 2006-01-13
frodon,
wow!  thank u very much!   Truly appreciate the guide! :smile:

---

### Post by ned.b on 2006-01-13
try this:

[https://wiki.ubuntu.com/MailServer?highlight=%28mail%29](https://wiki.ubuntu.com/MailServer?highlight=%28mail%29)

there are plenty of guides and documentation available on the wiki and also on the main documentation site:

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by kerang2k on 2006-01-13
ned.b,
Thank you very much for your help on those guides!  Really gives more option.  Wow, looking through the guide just now provided by frodon, setting up a mail server ain't easy as u need to be careful with the settings and steps.   Really pray if there is a simple ones :D

---

### Post by bscbrit on 2006-01-14
I have already configured a computer to act as a mail server, and it is not as difficult as you might first imagine.  Yes, there are loads of possible configuration settings but most can remain at the defaults.

How many users will your system have?  Will they use IMAP, POP or both?

I use fetchmail, postfix, procmail, spamassassin and clamav - it works like a dream and traps so much spam and virus traffic that I am horrified at how much is actually being sent to my multiple accounts.  But, the computer does the work so it isn't too much of a problem.

Let me know how far you have got. It is easiest to do it in stages e.g.

1. fetchmail, postfix and pop.

2. Add clamav

3. Add spamassassin

4. Use procmail to re-address multiple accounts to specific users.

etc....

---

