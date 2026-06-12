---
title: "Evolution setup"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by jrz on 2006-10-11
This is our 2nd day using Ubuntu Linux 6.06, and we are trying to figure out how to set up Evolution to retrieve email from Hotmail, Yahoo, and Gmail. It works fine on another notebook running Windows and Outlook Express, but we have yet to figure out how to do the same with Evolution if it is possible. If someone has such knowledge and could provide detailed instructions please do so as we have no idea how to proceed and are afraid of messing up the Linux OS as we have no idea how to recover from any mistakes, nor do we possess the software to reinstall as it is a Compaq V3012AU notebook which came pre-loaded with Linux. So far we have only been able to make it access the internet and that is all. Thank you.

---

### Post by jorn on 2006-10-11
First of all Welcome!
Just start evolution and follow the guide. Don't be afraid of messing up something. You learn by doing.

---

### Post by PriceChild on 2006-10-11
Here's the settings for gmail: [http://mail.google.com/support/bin/answer.py?answer=13287&topic=1555](http://mail.google.com/support/bin/answer.py?answer=13287&topic=1555)
Last thing i heard MS required payment to use outlook with hotmail, and other clients "wouldn't work". I'm not sure though as haven't used them in a couple of years.
Yahoo:
[http://help.yahoo.com/help/us/mail/ext/ext-07.html](http://help.yahoo.com/help/us/mail/ext/ext-07.html)

---

### Post by kevinlyfellow on 2006-10-11
If you really mess up your configuration in evolution, you can simply press ctrl-h in your home directory to uncover hidden files and delete .evolution and evolution's defaults will be restored.  I can't tell you about yahoo and hotmail, but I've done the gmail configuration and it does work well.  Here's what you do:

If you no longer get the initial configuration then go to edit -> preferences.

On that menu click add.

Enter the information on the first screen (name and email address) and hit the forward button

On the next screen use the dropdown menu and select POP.  Hit forward

This screen is a bit more tricky.  Choose SMTP (I think its default).  The server for gmail will be smtp.gmail.com and it requires authentication.  For the Security use SSL Encryption.  Your user name cannot have the @gmail.com part. Hit forward.

This screen should have your email address on it, make sure it doesn't have the @gmail.com part, hit forward

---

### Post by Sandlst on 2006-10-11
Try
 [http://www.ubuntuforums.org/showthread.php?t=200408&highlight=evolution+hotmail]("http://www.ubuntuforums.org/showthread.php?t=200408&highlight=evolution+hotmail")

for getting hotmail setup.

For yahoo, just run the wizard from evolution, using the info from this site:
[http://help.yahoo.com/help/us/mail/pop/pop-03.html]("http://help.yahoo.com/help/us/mail/pop/pop-03.html")

Ive heard if you have a yahoo email address in the US, you have to pay them $20.00 to use the POP3 service.  Alternatively, you could get a yahoo adress in another country (eg. getting a [email]xxxx@yahoo.co.uk[/email] for one in the United Kingdom)

Go here for help with GMAIL (scroll down to the evolution-specific part)
[http://www.ubuntuforums.org/showthread.php?t=231724&highlight=evolution+gmail]("http://www.ubuntuforums.org/showthread.php?t=231724&highlight=evolution+gmail")

Good luck, Post back if you have any problems.

---

### Post by jrz on 2006-10-11
Thanks, and we have spent the last 14 hours trying reading others posts and trying everything we can think of own our own and are still unable to access email using Evolution. About the only thing we feel confident of is our email address and password.
As far as we believe we have the information correct uner the Identity Tab, but are uncertain about the Receiving Email and Sending Email tabs where we have tried to identify the server as [http://services.msn.com/svcs/hotmail/httpmail.asp](http://services.msn.com/svcs/hotmail/httpmail.asp)
which is what we found to be used by Outlook Express.
For receiving email Server Type we have tried entering NONE, IMAP, and POP, and for sending email we have set it to SMTP.
Each time we try to run Evolution to collect email it fails and changes our server setting to just http for both sending and receiving.

I notice more responses have appeared since I started to type this so I will read them and see if they provide answers, but perhaps this message might show how little we know about what to do. Thanks everyone.

---

