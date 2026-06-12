---
title: "Unable to authenticate smtp server"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by cazmatazzz on 2007-12-23
Hey everyone, I have just set up Xubuntu on my moms computer but the only thing that I cannot for the life of me get working is to send **outgoing mail.** I have tried this in evolution, thunderbird and kmail; which all have the same problem, they can receive emails but not send any. 
the programs keep asking for the password, but when i fill in the correct password this is the error message i get: [COLOR="Purple"]Unable to authenticate to SMTP server.
Bad authentication response from server[/COLOR]. (in evolution, but similar responses in kmail and thunderbird)

as far as I believe all settings are correct (ie exchange plugin is installed)

this is what i got from terminal but i do not exactly know what to do with it:

charlotte@charlotte:~$ telnet smtp.xs4all.nl 1025
Trying 194.109.6.51...
telnet: Unable to connect to remote host: Connection timed out
charlotte@charlotte:~$ telnet smtp.xs4all.nl 25
Trying 194.109.6.51...
Connected to smtp.xs4all.nl.
Escape character is '^]'.
220 smtp-vbr1.xs4all.nl ESMTP Sendmail 8.13.8/8.13.8; Sun, 23 Dec 2007 15:23:04 +0100 (CET)

please help! this not being able to send email business is dreadful!

---

### Post by mellowd on 2007-12-23
What are the smtp servers required settings? It might require encryption. You'll need to get the specifics from the support department

---

### Post by Bachstelze on 2007-12-23
Maybe you're trying to use the wrong authentication method ? I don't know about others, but KMail can check which authentication method(s) the server supports, and display only those ones (see attached screenshot).

---

### Post by cazmatazzz on 2007-12-23
i am not entirely sure what the servers smtp settings are (and i will contact them, thanks) but i have tried without encryption and with encryption (SSL) still neither works, 

also i did the check of supported authentication types and tried all combinations, ie; when there is no encryption i can either use "login" or "plain", tried all of them 

and still, nothing works!

---

### Post by cazmatazzz on 2007-12-23
more information: the email my mom uses is an old webmail address, that uses the pop3.zonnet.nl account, outgoing server however has to be that of the internet provider, which is smtp.xs4all.nl 

maybe the problem could lie in that, but that would be very strange, because my computer (with configured hotmail account in evolution) uses the same internet connection without a problem!

---

### Post by mellowd on 2007-12-23
> **cazmatazzz said:**
> more information: the email my mom uses is an old webmail address, that uses the pop3.zonnet.nl account, outgoing server however has to be that of the internet provider, which is smtp.xs4all.nl 

maybe the problem could lie in that, but that would be very strange, because my computer (with configured hotmail account in evolution) uses the same internet connection without a problem!

It wouldn't be strange, as hotmails authentication process could be different from the .nl one.

---

### Post by mike555 on 2007-12-28
Just a thought , some mail systems want you to get mail before sending mail , I found that out because I used to type mail off line then go online and try to send , but it wouldn't until I tried to get mail from them first (that is the way they authenticate your user info) .........

---

