---
title: "SquirrelMail ERROR : Connection dropped by imap-server"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-03-15
Hello. I have just installed mailserver (SquirrelMail) on my Ubuntu Linux
webserver. I go to my webservers SquirrelMail address wich is
10.0.0.12/mail and the login page looks fine. But when I try to login
I get a error message.

I get the following error message when I try to login :
SquirrelMail ERROR : Connection dropped by imap-server

When I check the mail log under /var/log/mail.log it says :
Mar 15 18:24:36 localhost imaplogin: chdir Maildir: No such file or directory

Any suggestions on what is wrong and how I can fix it ?

---

### Post by Pragmatist on 2006-03-15
this should help:
[http://www.squirrelmail.org/wiki/MailDirError](http://www.squirrelmail.org/wiki/MailDirError)

---

### Post by chrisdee on 2006-03-15
It still doesnt work. Hmmm.

---

### Post by Pragmatist on 2006-03-15
What exactly did you try?

---

### Post by chrisdee on 2006-03-15
The guide you gave me said to install Qmail, but I did not find Qmail in Ubuntu
Synaptic Package Manager.

I tried to reinstall the Courier IMAP server but I get the same error message.

Where do I find and gow do I install Qmail ?
Will installing Qmail solve the problem ?

---

### Post by Pragmatist on 2006-03-15
Great news! As usual, the Ubuntu wiki comes through!

[https://wiki.ubuntu.com/Squirrelmail?highlight=%28mail%29](https://wiki.ubuntu.com/Squirrelmail?highlight=%28mail%29)

At first I thought the above link wouldn't help with the problem your experiencing.  Then, however, I started to follow the other links such as those under "prerequisites" like an MDA (Mail Delivery Agent--this is what Qmail is, but there are many others, as mentioned in these links)  So, if you go to the above link, read the prerequisites, see you need an MDA and go to this link:
[https://wiki.ubuntu.com/MailServer](https://wiki.ubuntu.com/MailServer)

Now you can read about dovecot, courier and cyrus as MDAs   This is not to be confused with MTAs (Mail Transfer Agents) which is something else (examples are: postfix, exim4) 

Anyway, check those out and if you have more questions we'll try and walk you through them.

---

### Post by chrisdee on 2006-03-16
Thank you for your reply. Iv followed the new guide you posted
a link to. Everything goes ok untill I try to start the Dovecot service.
I get the folloing error message : 

/etc/init.d/dovecot start
Starting mail server: dovecotFatal: listen(143) failed: Address already in use

How do I solve this ?

---

### Post by chrisdee on 2006-03-16
Anybody else have a solution to this problem ?

---

### Post by Pragmatist on 2006-03-16
You probably have more than one IMAP server running.  Go into synaptic 
```
sudo synaptic
```
and do a search with keyword **imap  **Or even better, do you remember if you installed an IMAP server previously?

Also, what version of Ubuntu are you using (breezy? dapper?)

---

### Post by chrisdee on 2006-03-16
Hello again. Now I removed all the other imap server that I by
newbie mistake installed. I actually got a bit further this time.
But I still get a error message, se below :

ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given:


So, what could be wrong now ?

By the way, I use Gnome Desktop ver. 2.12.1 and 
Linux T3 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux

---

### Post by Pragmatist on 2006-03-16
>  ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given:

What was the reason given?

---

### Post by chrisdee on 2006-03-16
Any suggestions ?

---

### Post by Pragmatist on 2006-03-16
>  			 				 ERROR : Could not complete request. Query: SELECT "INBOX" **Reason Given**:

What did it say after "Reason Given:"

---

### Post by chrisdee on 2006-03-17
Hello again. It doesnt give me any reason. It only says :

ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given: 

Any suggestions ?

---

### Post by chrisdee on 2006-03-17
I still have the same problem, so any suggestions are greatly apreciated.

---

### Post by chrisdee on 2006-03-17
Changed the topic.

---

### Post by Pragmatist on 2006-03-17
I would suggest starting over and trying these instructions:
[http://ubuntuforums.org/showthread.php?t=97600]("http://ubuntuforums.org/showthread.php?t=97600")

Also, it might help if you read through the posts here (all the forums). Just do a search from the main forums page using keyword: **squirrelmail**  Another search is to use part of the error message with or without the keyword squirrelmail.

You also might want to search through the ubuntu bug database (although probably not necessary at this stage):
[https://launchpad.net/malone/distros/ubuntu]("https://launchpad.net/malone/distros/ubuntu")

Finally, I would look through squirrelmail's documentation, and mailing-list archives, and I would subscribe to the mailing-list and post my question there.

---

### Post by brians78 on 2007-12-28
Hi folks!

   First post, but I had to share this.  I ran into the same error message.  Evidently when you are using postfix, there is no automatic creation of your maildir UNTIL you send the new account an email.  Once you send the email, everything should work just fine.  :)

[http://www.linuxquestions.org/questions/debian-26/squirrelmail-connection-dropped-by-imap-server-221427/](http://www.linuxquestions.org/questions/debian-26/squirrelmail-connection-dropped-by-imap-server-221427/)

Enjoy!:)

---

### Post by AlphaWu on 2008-04-19
Yes.
Thanks brians78

---

