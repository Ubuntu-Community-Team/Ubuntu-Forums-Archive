---
title: "[SOLVED] gmail + IMAP + evolution = communications :D"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-15
so how do I get this wonderful combination to work?
is there a howto for evolution that I could follow?

it tries to fetch mail at "username@imap.gmail.com" and it should be at gmail.com

hmm

SV

---

### Post by seventhc on 2007-12-15
these are the setting you need, I use gmail + imap + mutt, and it will work in evolution too.

oh, just noticed my link didn't post. well no need to repost as someone put them in.

but maybe i will anyway ;)
[http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814](http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814)


---

### Post by RomeReactor on 2007-12-15
Hi. Open Evolution, go to "Edit->Preferences", select your Gmail account and press "Edit"; on the "Identity" tab, make sure your email address is correct. In the "Receiving Email" tab:

* Server Type:  IMAP
* Server: imap.gmail.com
* Username: (your gmail account)
* Use Secure Connection: SSL encryption
* Authentication Type: Password

In the "Sending Mail" tab:

* Server Type: SMTP
* Server: smtp.gmail.com
* Check "Server requires authentication"
* Use Secure Connection: TLS encryption
* Authentication Type: PLAIN
* Username: (your gmail account)

If you're using Firestarter to manage your firewall, make sure ports 993 (Imaps) and 465 (Ssmtp) are open.

---

### Post by useResa on 2007-12-15
I believe that a combination of [this instruction]("http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/") and the information provided by Gmail ([enabling IMAP]("http://mail.google.com/support/bin/answer.py?answer=77695") and [configuring other mail clients]("http://mail.google.com/support/bin/answer.py?answer=78799")) should enable you to set this up.

Instead of where the instruction indicates to enter pop.gmail.com use imap.gmail.com and make sure you use the correct security settings and port information.

I hope this helps.

---

### Post by staticvoid on 2007-12-16
Hmm... its still not working, but I put all the settings as you said... I took the Gmail tutorial on doing it (they did not have one specific for evolution though)

in Gmail I have IMAP enabled..

I sent myself an email and it did not show up in evolution, it just appears as if I did not have any mail. I wonder if it is sending email properly... I'll test.

Oh wait! useRese, that is a great tut... [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

I'll try that and see how it goes :) I just opened your links, I thought they were all for the gmail tuts.


ciao

SV

---

### Post by staticvoid on 2007-12-16
argh... still not working

---

### Post by seventhc on 2007-12-16
When I was using evolution if I sent email from my own account, evolution didn't retrieve it. I had to send it from a secondary account so i sent from my yahoo to my gmail. If you've done this and it still didn't work then what errors are you getting? If you are not getting any errors, then most likely it is working.
If you want you can send a test to me and I'll reply to it.
same user as here in ubuntu at gmail. also try hitting the send/receive.

---

### Post by staticvoid on 2007-12-16
sent an email from yahoo.

no error and no message...

so wierd!  :P

i might have to use pop :(

sv

---

### Post by staticvoid on 2007-12-16
and no firestarter, so my ports should be open...

---

### Post by useResa on 2007-12-16
For my work we have an IMAP server and this works great in evolution.
Let me indicate what I think should be your settings:

"**Receiving Email**" tab:
*Server type:* IMAP
*Server:* imap.gmail.com:993
*Username:* your gmail username
*Use secure connection:* SSL Encryption
*Authentication type:* Password

"**Sending Email**" tab:
*Server type:* SMTP
*Server:* smtp.gmail.com:465  or smtp.gmail.com:587
*Use secure connection:* SSL Encryption
*(Authentication) Type:* Login
*Username:* your gmail username

I hope that this will help you to get it working.
Just for confirmation: Do you have the port numbers mentioned after the server name?

---

### Post by seventhc on 2007-12-16
You also have to enable imap in gmail. log into your gmail account click on [COLOR=Blue]settings[/COLOR] then '[COLOR=Blue]Forwarding and POP/IMAP[/COLOR]' scroll down and make sure '[COLOR=Blue]enable IMAP[/COLOR]' is checked. [COLOR=Blue]Save Changes[/COLOR] then try again.

---

### Post by staticvoid on 2007-12-16
I did that... still no go...

any more ideas? can I some how check mail from the terminal with evolution and see output errors? even though they are not listed...


sv

---

### Post by seventhc on 2007-12-16
On the left side there are folders, click on them. I just set mine up and had to open a folder otherwise it looked as if I had no mail. but here are some screenshots of setup. look at everything
check your server type, your security options, if you match these it should work. Mine did

---

### Post by staticvoid on 2007-12-16
thank you so much for your time and effort seventhc! It worked!

Well, actually, I think it may have been working before I just notticed a [email]username@gmail.com[/email] account in the side bar, i was looking in the inbox for my local files. which is where pop went. huh.

Now I see Gmail folder, etc. I guess IMAP looks different then POP, lol.
heres some screen shots

sv

---

### Post by seventhc on 2007-12-16
Glad that you got it:) I think it was working too since you weren't getting any error's and yes it does look different using IMAP over POP but IMO IMAP is better. :)

---

### Post by id3379 on 2008-01-08
Thanks RomeReactor, Worked Perfect ! :)

---

### Post by akarimco on 2008-02-01
I have a question about this... is there any way to archive the email (without deleting it) but from Evolution?

---

### Post by seventhc on 2008-02-01
If your using it with IMAP you should see the 'All Mail' folder which is the archive.

---

### Post by staticvoid on 2008-02-02
same with thunderbird

---

### Post by funkyhat on 2008-05-08
> **akarimco said:**
> I have a question about this... is there any way to archive the email (without deleting it) but from Evolution?

pressing delete will remove the message from the folder/label you are currently looking at, so if you delete something from inbox that is the same as archiving it in gmail
If you want to actually delete it drag it to 'bin'

---

