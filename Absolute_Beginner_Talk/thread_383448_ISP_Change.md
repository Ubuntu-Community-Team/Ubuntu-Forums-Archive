---
title: "ISP Change"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2007-03-13
I have recently changed from ntlworld dialup to TalkTalk Broadband problem is on the Mail side of things it doesnt seem to recognise my password for incoming mail.I can send it okay.Any ideas out there.Many thanks

---

### Post by milton1 on 2007-03-13
What are you using for mail service? POP/SMTP? IMAP? Webmail? If it is POP, I suggest you try another POP capable service (gmail, etc.) to see if the problem is local or not. Could be that your password was saved incorrectly by your isp. Could be that a port is blocked. Could be many things.

---

### Post by kolinab on 2007-03-13
Like milton1 says, we need to know a little more about your email problem. Are you using Evolution or Thunderbird or some other email client, or are you sending email with a webmail type interface? Are you trying to use a new email account created by your new provider? Once you tell us what you're using to access your email we can hopefully tell you how to change/erase your old password etc. from your preferences and get it reset to the new one.

Let us know how it goes.

---

### Post by bobanshirl on 2007-03-13
I am using pop/smtp and I have tried Evolution and Thunderbird why is it such a chore to sort out the email,I log on straight away I browse the internet I can send emails but surely you would think I could receive as well.Heres hoping

---

### Post by milton1 on 2007-03-13
are you getting a specific error message? Password invalid? server not found?

---

### Post by kolinab on 2007-03-13
No problem - we should be able to sort this out. Likely the reason why you can send without difficulty is that lots of SMTP servers don't require a password to send mail if your accessing the internet through their servers. 

SO - for your sending problem, I can really only help you with Thunderbird since it's what I'm familiar with, but the process should be similar in Evolution I would think. In Thunderbird, go to Edit . . . Account Settings. Then click on 'Server Settings.' Have a look in there (I bet you have!). Check to see that your username is correct and that the name of your POP server is correct as well. Sometimes an ISP will have you connect to their POP server on a particular port - and with particular security settings. 

Check the help pages for your TalkTalk Broadband service - there should be a page somewhere there telling you how to set up various email clients. Even if the instructions are for some silly program like Outlook Express, you should be able to glean the necessary information from those pages.

One word of note - if you are trying to access a POP account from an other ISP (like a work account, or from your old ISP) you might encounter problems. Like SMTP, many servers won't let you access POP unless you come from an IP address on their system.

That's kind of some basic troubleshooting info. What are the particulars of the error message you get when trying to send mail?

Also - in T-bird go to Edit . . . Preferences . . . Privacy . . . Passwords . . . and click on 'View Saved Passwords.' Click 'Remove All' to start from scratch. Maybe there was a typo when you initially keyed in your password and Thunderbird keeps trying to use the wrong one.

Let us know how you do - this is a simple enough problem, we'll get to the bottom of it.

---

### Post by IanGB on 2007-03-13
I use TalkTalk and all you need to know for either email program is that the Server send  address is: mail.talktalk.net and the receive is: smtp.talktalk.net

These are entered in your Account settings from the Edit menu.

Your log in for connection is your phone number as your username:  [email]01424000000@talktalk.net[/email] for instance and your chosen password.

Both should have arrived by email from TalkTalk.

You would also have been invited to chose an alternative email address or up to six extra one's I believe, where you just chose the name before the @

Ian

---

### Post by bobanshirl on 2007-03-14
Thanks for all your help I tried most things deleted account reinstalled this was yesterday still no joy this morning tried again and to my surprise when I clicked on Receive Email voila or eureka anyway its all tickety boo now.Cheers.

---

### Post by kolinab on 2007-03-14
Happy emailing!

---

