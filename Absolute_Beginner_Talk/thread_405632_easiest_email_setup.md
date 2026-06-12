---
title: "easiest email setup"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jammodotnet on 2007-04-10
Hi all.
I'm a hobbyist web developer.
I just recently followed a tutorial on installing php, mysql, phpadmin and apache2 on my Ubuntu machine. Everything is working fine fine fine ... except one thing!!!

I'm tinkering with ExpressionEngine (a powerful php cms), but have somehow logged myself out of the admin section. I know i HAVE THE RIGHT PASSWORD, but it just refuses to let me log in.
This is NOT an ExpressionEngine issue.

Just like all CMS type systems, there is a, "Forgot your password?" link in the admin section.
Everytime I click it, it results in an error, that email can not be sent.

I assume it's because I do not have some email server installed?

I don't want something to send emails to anyone, just for local offline development.
I did some reading about Postfix, and it seems to be too 'big' of something to install for me.
Any simpler alternatives?

---

### Post by hockey97 on 2007-04-10
Well I think postfix is mostly used for linux type servers ect so it has alot of support which to me makes it easy to install, however their are many other mail servers one is 
Courier Mail Server and many others you can google mail servers you will find many.
But when you click that forgot password link did you check in the script where it's trying to connect becuse it's good to know becuse when you do get the mail server you would have to point that link to the mail server and to a user ect. If you want something really easy to setup like with little modding to config files ect then I would say squirrelmail
I never tried it myself only recommending it to you based off other users that used it said it was easy to install and with little config modding files.
[http://www.squirrelmail.org/]("http://www.squirrelmail.org/") website to download it if wanted...

hope this somewhat helps.

I posted this seening that no one posted a response on here.

---

### Post by jammodotnet on 2007-04-11
thanks for the recommend hockey97.
i'm looking into it now.

---

### Post by jammodotnet on 2007-04-11
WHOA! WOW! :eek:

i dont think ill be travelling the route of postfix. it's just too darned complex looking to attempt.

over on the expression engine forums, i read that my problem could stem from a cookie issue. ill be testing that out later tonight.

as for my email capabilities, i suppose when i REALLY NEED IT, ill force myself to install Postfix and get it working.
shoot!!! i got php, mysql, apache and phpmyadmin to work, flawlessly, thanks to the indepth docs on the site.
:)
thanks again

---

### Post by kvonb on 2007-04-11
I use postfix and dovecot for my fully fledged email system, it's really not that hard (I did it so it must be easy! :) ).

All you have to do is change a few things in the config file like your server name and stuff.

I can send you my config file if you like, then just change the bits you need.

Regards, Kev :)

---

### Post by heimo on 2007-04-11
I've been wrong before, but in this case I have a strong instinct that configuring smtp server will have any effect on letting jammodotnet log into ExpressionEngine.

> have somehow logged myself out of the admin section. I know i HAVE THE RIGHT PASSWORD,Are you saying it worked before?

Error about not being able to send mail, may need config changes in PHP and/or ExpressionEngine. Here's how to configure postfix.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

There's also usually way to reset / set your password without web-userinterface - if you know where the password or its hash is stored. (probably in database, in some cases admin password may be in a config file)

---

### Post by jammodotnet on 2007-04-11
> **kvonb said:**
> I use postfix and dovecot for my fully fledged email system, it's really not that hard (I did it so it must be easy! :) ).

All you have to do is change a few things in the config file like your server name and stuff.

I can send you my config file if you like, then just change the bits you need.

Regards, Kev :)could you really?
i mean, send the config so i can see how it's done?
i downloaded/installed through Synaptic, Postfix and the Docs.
i just dont know where to find it, how to config it, etc.
seeing how you did things might help me out!

> **heimo said:**
> There's also usually way to reset / set your password without web-userinterface - if you know where the password or its hash is stored. (probably in database, in some cases admin password may be in a config file)actually YES there is.

i went so far as to set up a fresh installation of expression engine in a different directory and made my account as usual. then copied the appropriate database fields from the new EE install, to my troubled one.


it DIDNT work, but guess what?
on my expression engine forums help request? we discovered it was a cookie problem.
since i have FTPed everything down from my live site to my development site (files + database), i made all the necessary DB changed, but i over looked cookies and a few minor things.
lmao.

i feel like such an ***.



concerning the issue with installing Postfix, i just wanna be clear, i have no intention to set up a mail server (like to send mail to friends and receive), i just need something that will allow my expression engine installation function fully: send/receive PMs via EE control panel, send mailing list email, recover password, validate new members.
am doing a complete site build and test and evaluation of ExpressionEngine. :)

---

### Post by hansi70 on 2007-04-11
Hi,

I am also a newbie and I have installed postfix. I am not sure how to set it up to test it on a localhost without a  domain name (I don't own a domain name). 


Can you please send me the config file? Also can I create a dummy domain name with localhost for email testing purposes and can I link postfix with an email client such as Thunderbird mail?

Sorry for the many questions,

Regards,
Hansi
 

> **kvonb said:**
> I use postfix and dovecot for my fully fledged email system, it's really not that hard (I did it so it must be easy! :) ).

All you have to do is change a few things in the config file like your server name and stuff.

I can send you my config file if you like, then just change the bits you need.

Regards, Kev :)

---

### Post by kvonb on 2007-04-12
Here are my config files from dovecot and postfix.

There's not much to do with dovecot, just make it default to POP3 I think, and I have put a long line of asterisks before each line that was modified in main.cf which goes in /etc/postfix/.

I use a free dynamic hostname from [www.dyndns.org]("http://www.dyndns.org") and it works perfectly, I can send and receive emails perfectly.  I didn't have to do much at all, it just worked!

Oh, you will need to create (or already have) each user that you want to send/receive mail on the same computer that is running postfix.  And each account MUST have a ~/Maildir folder in it for the mail server.  I simply made a folder as root in /etc/skel/, ie:

```
sudo mkdir /etc/skel/Maildir
```that way each time you add a new user the Maildir folder will be created automatically.

Hope that lot helps :)

---

### Post by hansi70 on 2007-04-12
Hi ,

Thanks a lot for your kind and generous help. If I can ask another question:  I have managed to set up postfix to work as a local mail server so that I can send a test email to an account on the same machine (without an internet connection). For example, I can send an email to dude@localhost and it works. I want to create a dummy local domain name (alias?) that can act as a substitute to localhost (e.g. example.com) and can works without an internet connection. Is it possible to do this?

Regards,

Hansi   

> **kvonb said:**
> Here are my config files from dovecot and postfix.

There's not much to do with dovecot, just make it default to POP3 I think, and I have put a long line of asterisks before each line that was modified in main.cf which goes in /etc/postfix/.

I use a free dynamic hostname from [www.dyndns.org]("http://www.dyndns.org") and it works perfectly, I can send and receive emails perfectly.  I didn't have to do much at all, it just worked!

Oh, you will need to create (or already have) each user that you want to send/receive mail on the same computer that is running postfix.  And each account MUST have a ~/Maildir folder in it for the mail server.  I simply made a folder as root in /etc/skel/, ie:

```
sudo mkdir /etc/skel/Maildir
```that way each time you add a new user the Maildir folder will be created automatically.

Hope that lot helps :)

---

### Post by kvonb on 2007-04-13
I'm a little out of my depth here, I was extremely lucky to get my email server working, and can't remember the actual steps I took to get it going!

I have a suggestion though, maybe edit /etc/hosts and on the line that contains "localhost", simply add "example.com" to the end like so:

```
127.0.0.1 localhost example.com
```

Then in /etc/postfix/main.cf change your domain to example.com and restart.

That might work!

Regards, Kev :)

---

### Post by hansi70 on 2007-04-13
Yes it did!

You are a genius man! Thanks a lot! 

Hansi


> **kvonb said:**
> I'm a little out of my depth here, I was extremely lucky to get my email server working, and can't remember the actual steps I took to get it going!

I have a suggestion though, maybe edit /etc/hosts and on the line that contains "localhost", simply add "example.com" to the end like so:

```
127.0.0.1 localhost example.com
```

Then in /etc/postfix/main.cf change your domain to example.com and restart.

That might work!

Regards, Kev :)

---

### Post by kvonb on 2007-04-13
Just a lucky guess ;)

---

### Post by heimo on 2007-04-13
Just for record. example.com/net/org is fine, when testing. Do not use any existing domain (which is not actually yours/controlled by you) or any non-existent domain for this purpose (except top level domains listed also in the RFC2606).
[http://www.rfc-editor.org/rfc/rfc2606.txt](http://www.rfc-editor.org/rfc/rfc2606.txt)

---

### Post by hansi70 on 2007-04-14
Hi Kvong,

You should play the lottery :).

Regards,

Hansi

---

### Post by hansi70 on 2007-04-14
Hi,

Thanks Heimo. I will only use example.com.

Regards,

Hansi


> **heimo said:**
> Just for record. example.com/net/org is fine, when testing. Do not use any existing domain (which is not actually yours/controlled by you) or any non-existent domain for this purpose (except top level domains listed also in the RFC2606).
[http://www.rfc-editor.org/rfc/rfc2606.txt](http://www.rfc-editor.org/rfc/rfc2606.txt)

---

