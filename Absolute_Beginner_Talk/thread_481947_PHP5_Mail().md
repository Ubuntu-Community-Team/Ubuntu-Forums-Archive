---
title: "PHP5 Mail()"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by doyler78 on 2007-06-23
I have MailEnable installed on windows vista ultimate pc which I use to manage mail for the 3 domains which I have purchased. I have been using it for a long time and I am familiar with reading the log files, etc. My intention is eventually to move my mail server to Ubuntu however as I have only started using linux I do not feel comfortable doing so now. Once I become more familiar with linux I will then start to think about the move. Having said that I did install postfix, courier, courier-imap, courier-imap-ssl, courier-pop, courier pop-ssl, fetchmail via guides howtoforge.net. However I haven't opened any of the ports relating to the services in firestarter and my router maps the mail ports to my Vista machine.

My Vista pc is on 10.0.0.4
My Ubuntu machine is on 10.0.0.1

My php.ini under /etc/php5/apache2/php.ini has been amended to:

```
[mail function]
; For Win32 only.
SMTP = 10.0.0.4
smtp_port = 25

; For Win32 only.
sendmail_from = [EMAIL="webmaster@mydomain.net"]webmaster@mydomain.net[/EMAIL] 
```When I run phpinfo.php on the ubuntu webserver I see the following entries:

```
SMTP               10.0.0.4
smtp_port          25
```There is also line sendmail_from: which correctly gives [EMAIL="webmaster@mydomain.net"]webmaster@mydomain.net[/EMAIL]

However there is the following entry as well:

```
sendmail_path              /usr/sbin/sendmail -t -i
```Basically I thought when I had specified the SMTP Server and port to use in the php.ini file that php scripts using mail() would use this server however they don't. They send via postfix. Anything to external addresses ie not in my static ip address gets sent however anything to mydomain.net mail accounts doesn't get delivered. I know this is because when it is trying to send it is trying to send to those addresses by using the external ip and not the internal one ie not 10.0.0.4. I can tell this by looking in Webmin at the postfix config screen in servers section which shows mail queue info. It has entries showing my messages which show connection timed out next them and my static ip address next to it rather 10.0.0.4.

I amended the hosts file to try and correct this by putting the following entries:

mail.mydomain.net        mydomain.net

If I stop postfix then no php mail gets delivered.

Other things I have tried. I can telnet 10.0.0.4 25 and get a response from my MailEnable Server.

I can telnet to mydomain.net 25 and get a response from my MailEnable Server

I can telnet to mail.mydomain.net and get a response from my MailEnable Server.

I have even allowed 10.0.0.1 relay options on my MailEnable SMTP Server but that hasn't made any difference. The reason being that at the min php isn't even trying to use MailEnable it is using postfix.

As you can probably see I am very confused. Only new to trying this stuff. Well you have to start somewhere.

---

### Post by doyler78 on 2007-06-23
Nobody any ideas why php mail() ignores php.ini (at least that's what I presume is wrong) or where I might have gone wrong.

---

### Post by octoberdan on 2007-06-23
> **doyler78 said:**
> Nobody any ideas why php mail() ignores php.ini (at least that's what I presume is wrong) or where I might have gone wrong.

This sort of question is sort of unusual for this part of the forum. Perhaps try 

Server & Security: [http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)
or
General Help: [http://ubuntuforums.org/forumdisplay.php?f=131](http://ubuntuforums.org/forumdisplay.php?f=131)
or
Programming Talk: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by doyler78 on 2007-06-23
Thanks - moved it now to Servers & Security.

---

