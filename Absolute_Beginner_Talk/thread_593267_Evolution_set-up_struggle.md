---
title: "Evolution set-up struggle"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Ned183 on 2007-10-27
UBUNTU people, I've installed Feisty Fawn. Everything seems fine, it recognized all my stuff, etc and I'm on the web. My question concerns the Evolution email thingy. I have two email accounts; one with fishhoo.com and one with bigstring.com. The evolution set-up pages seem to need more information than I am able to get from either account. I feel like I am missing something quite simple here but I need some help. Please, don't send me back to Mister Gates. Anyone?
Ned

---

### Post by Halfling Rogue on 2007-10-27
Couldn't you just use Thunderbird?

---

### Post by Frak on 2007-10-27
Save some trouble and use Thunderbird.

---

### Post by Daveth on 2007-10-27
oo, come on there in nothing wrong with evolution. I guess the bits of information you need are related to the pop3 and smtp server names. Your provider should be able to give you those and they may well be on their web-site.

It will be something like pop3.fishhoo.com  and smtp.fishhoo.com, and you just enter those into the receiving and sending tabs in the account setup. Add your e-mail address in as well at the identity tab.

---

### Post by dfmalh on 2007-10-29
Hi Ned183, I am not familiar with either of the two "email providers".

From a link on the Bigstring site: "You can have POP3 access to your Bigstring account if you are a Premium member"

But maybe I can help you with the "Bigstring" account :-)

Also see this setup for XP... it usually contains everything you need to setup in Evolution:
[http://www.bigstring.com/userguides/setup/outlookxp_graphical.html](http://www.bigstring.com/userguides/setup/outlookxp_graphical.html)

When you do the Evolution mail setup, do the following:

_Receiving emai details_l:

Server type = POP
Configuration = server = mail.bigstring.com
Configuration = User Name = [email]username@bigstring.com[/email]
Security = no encryption
Authentication = Your Password (try and Authenticate, this would give you an idea if it will work)

_Sending emai details_l:

Server type = SMTP
Server Name = mail.bigstring.com
Security = no encryption


This is the basic configuration for most POP accounts. You will have to check the security on the servers (the host), maybe that will have to be different than the above setup.

If this does not help, email Bigstring and ask them what the settings should be for Evolution.

Hope this helps.

---

### Post by soggy on 2007-11-10
Hi,
I too am having trouble with the server configuration for Evolution (2.6.1).  I know the settings from my accounts, but I just can't find where to enter the account password.  The Receiving mail tab has a box to enter Server and UserName, but no box for password.  There's the box to check for Evolution to remember my password, but no where do I see to enter the password. I don't see an "Authentication" box (as mentioned by dfmalh) for entering my password. I know I must be missing something that's right in front of me, but I'm just not seeing it either in the actual screens or in the setup help information.  Thanks.

---

### Post by torgrot on 2007-11-10
As I recall there isn't a place during setup to add the passwords.  Just add the accounts without the password.  The first time you send/recieve in Evolution it will prompt for the password for each account.  Type it in and make sure that remember passwords is checked.  After that it won't prompt for that account again.

torgrot

---

### Post by hiloguy on 2007-11-10
Another vote for Thunderbird! I struggled with trying to get Evolution to be user-friendly in setup and then in operation and finally tossed it and installed Thunderbird.  Way better in every way, IMHO.

Why fight Evolution if it isn't working for you?

---

### Post by soggy on 2007-11-10
Thanks torgrot.  I started to suspect that it might be something like that.  The computer was given us with only a dialup modem so I haven't been able to connect it up yet to our DSL service.  Sounds like the issue will resolve itself once I get the network card in and the computer hooked up to the web.  thanks for the help.  I appreciate the guidance on Thunderbird as well.  I have it on my other PC but I haven't found it as useful (as, I hate to say, Outlook) for integrating tasks, meetings, and email.  So I wanted to give Evolution a fair try.  Plus, it's came with the installation and adding more software without direct internet connectivity is a step I'd rather avoid.

---

