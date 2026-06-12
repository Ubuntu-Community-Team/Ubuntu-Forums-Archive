---
title: "Using/Configuring Evolution in Breezy"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-03-02
Hi Everybody

I have 2 email addresses - one through Gmail and the other through Lycos.

Both provide POP3 access to email using email clients. I, in Windows use Outlook as my Email client to receive and send emails and it works ok.

Using the same settings, can I use Evolution in Ubuntu to access my emails from these accounts or does these POP3 access not work with Evolution?

Can anyone give me some pointers/suggestions as to how can I go about configuring Evolution so that I can access my emails from Gmail and Lycos through Evolution?


Best regards


Deepak Agarwal

---

### Post by jon_gunnar on 2006-03-02
[QUOTE=agarwaldvk]Hi Everybody

I have 2 email addresses - one through Gmail and the other through Lycos.

Both provide POP3 access to email using email clients. I, in Windows use Outlook as my Email client to receive and send emails and it works ok.

Using the same settings, can I use Evolution in Ubuntu to access my emails from these accounts or does these POP3 access not work with Evolution?

Can anyone give me some pointers/suggestions as to how can I go about configuring Evolution so that I can access my emails from Gmail and Lycos through Evolution?


Best regards


Deepak Agarwal[/QUOTE]

Know nothing about lycos,but getting evolution to fetch you're mail from gmail with pop is no problem.
Just set up a new account and fill in the info.All neccesary info is found in settings / Forwarding and POP I think if you log in to your'e gmail account.

Incoming Mail (POP3) Server - requires SSL:  	pop.gmail.com
Use SSL:   Yes
Port:        995
Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587
Account Name: 	 your Gmail username (including '@gmail.com')
Email Address: 	   your full Gmail email address (username@gmail.com)
Password: 	    your Gmail password

---

### Post by agarwaldvk on 2006-03-02
Dear Jon Gunnar

You Beauty! Thanks a lot!

This is what I like - when things are just pure (unadultrated) and simple.

I shall try that tonight and see how I go!


Best regards


Deepak Agarwal

---

