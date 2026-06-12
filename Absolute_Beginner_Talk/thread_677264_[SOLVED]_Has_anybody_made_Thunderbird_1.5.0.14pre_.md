---
title: "[SOLVED] Has anybody made Thunderbird 1.5.0.14pre work with gmail?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2008-01-24
I'm trying to make Thunderbird 1.5 which I got from Synaptic to use IMAP on my gmail account.
I have followed this tutorial:
[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

But it doesn't work is it really necessary to install Thunderbird 2.0 in order to make IMAP work?
I get this error when following that tutorial precisely:

[COLOR="Red"]Invalid credentials (Failure)[/COLOR]
Followed by this error when I click the close button:
[COLOR="Red"]Login to server imap.gmail.com failed.[/COLOR]

But when I change the Security settings to TLS instead of SSL in order to match my SMTP setting TLS I get this error.
[COLOR="Red"]Connection to server imap.gmail.com timed out.[/COLOR]

---

### Post by sirgogo on 2008-01-24
Hey Jingo,

I use Thunderbird 2.0 with my gmail account. I'm not sure, but I think the settings Google provides for Thunderbird is specific to the release because I remember I had to change the settings (ports) when I was using my Windows computer and had upgraded from 1.5 to 2.0.

However, I did have trouble with Thunderbird 1.5 in Ubuntu a while back, but I'm not sure its related because I think I had a faulty install.

---

### Post by newbeeman on 2008-01-24
> **jingo811 said:**
> I'm trying to make Thunderbird 1.5 which I got from Synaptic to use IMAP on my gmail account.
I have followed this tutorial:
[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

But it doesn't work is it really necessary to install Thunderbird 2.0 in order to make IMAP work?
I get this error when following that tutorial precisely:
[]

I would make sense to upgrade to V2 then go to Gmail and use the info from the setup files.
I would suggest your Synaptic is out of date, mine delivers version 2.0.0.6 and works just fine with Gmail.

---

### Post by gruss on 2008-01-24
thunderbird 2 should come out of synaptic, but i have 1.5.? on a thumb drive (windows version though) that works with imap.  dont know whats different feature wise bwtween the ports

---

### Post by jingo811 on 2008-01-25
How can I upgrade my synaptic without upgrading the entire Feisty 7.04 system to Gutsty 7.10?
My synaptic doesn't give me Thunderbird 2.0 :confused: even when I do these in CLI.
> sudo apt-get update
sudo apt-get upgrade

---

### Post by stchman on 2008-01-25
I have a script that installs Thunderbird 2.0.0.9 for Feisty or Gutsy.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Go to the Scripts section.

---

### Post by jingo811 on 2008-01-25
I don't get it even with Thunderbird 2.0 I get credential failure when typing in my password :confused: Do you guys get this when you're asked to enter the password?

> **Mail Server Password Required**

Enter your pasowrd for [email]myemail@gmail.com@imap.gmail.com[/email]:

I managed to change things like this but still I get "Invalid credentials failure".
> **Mail Server Password Required**

Enter your pasowrd for [email]myemail@imap.gmail.com[/email]:

---

### Post by andrewjoy on 2008-01-25
Have a look at this

[http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814](http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814)

its the standard config you can use for any IMAP cliant / device.

---

### Post by erm4gh on 2008-01-25
[http://kb.mozillazine.org/Using_Gmail_with_Thunderbird_and_Mozilla_Suite](http://kb.mozillazine.org/Using_Gmail_with_Thunderbird_and_Mozilla_Suite)

---

### Post by jingo811 on 2008-01-26
> **andrewjoy said:**
> Have a look at this

[http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814](http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814)

its the standard config you can use for any IMAP cliant / device.

Tnx that did the trick.
The outgoing mail wasn't TLS like the previous Google guide said the right answer should be SSL.
And "account Name" needs to be the same as the email field.

```
Outgoing Mail (SMTP) Server - requires TLS:  	smtp.gmail.com (use authentication)
se STARTTLS: Yes (some clients call this SSL)

Account Name: 	your Gmail username (including @gmail.com)
```

---

