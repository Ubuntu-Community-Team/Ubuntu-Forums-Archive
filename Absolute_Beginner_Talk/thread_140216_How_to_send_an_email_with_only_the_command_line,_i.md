---
title: "How to send an email with only the command line, in a script ??"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-05
How to send an email with only the command line, in a script ??
==============
  
Goal: To report daily nfo via email  (via a script)
  
Thank you !!
  
Patrick

---

### Post by patrick295767 on 2006-03-05
```
echo "myaddress@fdljfmdljsk.com" > ~/.forward
echo "message bla bla" > message.txt
mailx -s "subject" myaddress@fdljfmdljsk.com < message.txt
```
  
This is not workign ... 

No idea ?

---

### Post by ubuntumaneh on 2006-03-05
mailx is the name of the package. Therefore, if there is not in your system already (check it with dpkg -l| grep mailx)

sudo apt-get install mailx

Furthermore, the command for mail is simpler: just mail. So:

echo "myaddress@fdljfmdljsk.com" > ~/.forward
echo "message bla bla" > message.txt
mail -s "subject" [email]myaddress@fdljfmdljsk.com[/email] < message.txt

For send mail from time to time, check cron.

---

### Post by patrick295767 on 2006-03-05
[QUOTE=ubuntumaneh]mailx is the name of the package. Therefore, if there is not in your system already (check it with dpkg -l| grep mailx)

sudo apt-get install mailx

Furthermore, the command for mail is simpler: just mail. So:

echo "myaddress@fdljfmdljsk.com" > ~/.forward
echo "message bla bla" > message.txt
mail -s "subject" [email]myaddress@fdljfmdljsk.com[/email] < message.txt

For send mail from time to time, check cron.[/QUOTE]
  
I isntalled mailx before
and thsi is not working:
 ```
echo "myaddress@fdljfmdljsk.com" > ~/.forward
echo "message bla bla" > message.txt
mail -s "subject" [email]myaddress@fdljfmdljsk.com[/email] < message.txt
```
 (I replaced everthg correctly) 
 (i am not too newb to linux (or not first day of it))  

no email received into my [email]patrick295767@hotmail.com[/email] mailbox .... 
How ot do it ??

Thank you

---

### Post by patrick295767 on 2006-03-05
Is this webpage helping a bit : [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
  
I am not understand how i'll make it ... 

Greetz

---

### Post by patrick295767 on 2006-03-07
An idea, Someone ??

---

### Post by Pragmatist on 2006-03-07
First things first.  Before writing a script, can you use mail or mailx to send just one email?

---

### Post by Pragmatist on 2006-03-07
Also, what exactly do you want to do?  Do you have the message you want to send to everybody in the form of a file or from the screen?  Are the people you are forwarding this info to all listed in one file?  Are they one address per line?  Are you the only one sending the info or is any member of your forwarding list able to send a message and have it routed to everybody else??

---

### Post by patrick295767 on 2006-03-09
Thanks for ur concern ! :-) 

The first goal was to be able to send one email to my email address: 
[email]patrick295767@hotmail.com[/email] 
  
I tried sendmail but couldnt manage to send any to my email address via single cmd line. 
  
In order to do so, do I have to set up any smtp configuration somewhere ? 
  
I installed postfix and read that was teh easiest ... 
even though, I didnt manage ... 
  
I did : ps -ax | grep sendmail
and it appeared that there was a queue of non sent email to [email]patrick295767@hotmail.com[/email] ... 
  
I am stuck for the moment ... 

Greetings & thank you by advance !

Patrick

---

### Post by Pragmatist on 2006-03-09
I doubt that hotmail allows you to connect with your own client if you only have their free account.  You might try these guys: [http://www.fastmail.fm/](http://www.fastmail.fm/)
Although even here, notice that their free acount doesn't have SMTP; it just has a web interface like hotmail.  However if you pay them a one-time fee of $15, you can have SMTP.  Incidentally, I got the full membership for $20/year and even though it has POP access (hotmail is POP3), when I tried it hotmail gave me a message telling me they won't allow it with their free accounts.

Maybe if you search around you'll find a free one that will let you do SMTP.

---

### Post by az on 2006-03-09
I can mail myself something to my yahoo.ca mailbox using mail -s .  When I look at the headers, the sender is "localhost".  I seem to remember that I cannot send something to my wife's hotmail account because they do not accept mail from unregistered domain names.

I am not at home right now to confirm this, though.

---

### Post by patrick295767 on 2006-03-09
[QUOTE=azz]I can mail myself something to my yahoo.ca mailbox using mail -s .  When I look at the headers, the sender is "localhost".  I seem to remember that I cannot send something to my wife's hotmail account because they do not accept mail from unregistered domain names.

I am not at home right now to confirm this, though.[/QUOTE]
  
Aaaaaaaaaahhh ! Thank you ! 
  
I tried gmail & hotmail and nothing .. .so maybe that 's this 'cos of no unregistered domain names .. ;

---

### Post by az on 2006-03-09
[QUOTE=patrick295767]Aaaaaaaaaahhh ! Thank you ! 
  
I tried gmail & hotmail and nothing .. .so maybe that 's this 'cos of no unregistered domain names .. ;[/QUOTE]
I'll try later on with my yahoo account, just to be sure....

---

### Post by patrick295767 on 2006-03-09
after a tail :    ```
  tail -f /var/log/mail.info
```


```
ection timed out (port 25)
Mar  9 22:24:49 localhost postfix/smtp[16152]: connect to mx4.hotmail.com[65.54.245.104]: Conn
ection timed out (port 25)
Mar  9 22:25:14 localhost postfix/smtp[16151]: connect to mx4.hotmail.com[65.54.245.104]: Conn          ection timed out (port 25)
Mar  9 22:25:14 localhost postfix/smtp[16151]: 57B2620173: to=<patrick295767@hotmail.com>, rel          ay=none, delay=483, status=deferred (connect to mx4.hotmail.com[65.54.245.104]: Connection tim          ed out)
Mar  9 22:25:15 localhost postfix/smtp[16154]: connect to mx1.hotmail.com[65.54.244.8]: Connec          tion timed out (port 25)
Mar  9 22:25:15 localhost postfix/smtp[16154]: BB2D920177: to=<patrick295767@hotmail.com>, rel          ay=none, delay=481, status=deferred (connect to mx1.hotmail.com[65.54.244.8]: Connection timed           out)
Mar  9 22:25:19 localhost postfix/smtp[16152]: connect to mx4.hotmail.com[65.54.244.104]: Conn          ection timed out (port 25)
Mar  9 22:25:19 localhost postfix/smtp[16152]: D68CC20172: to=<patrick295767@hotmail.com>, rel          ay=none, delay=487, status=deferred (connect to mx4.hotmail.com[65.54.244.104]: Connection tim          ed out)
Mar  9 22:25:39 localhost postfix/smtpd[16328]: connect from localhost.localdomain[127.0.0.1]
Mar  9 22:25:40 localhost postfix/smtpd[16328]: 2481520179: client=localhost.localdomain[127.0     
```

---

### Post by patrick295767 on 2006-03-10
[QUOTE=azz]I'll try later on with my yahoo account, just to be sure....[/QUOTE]
   
Thank you Azz !!
  
You can use : 
 tail -f /var/log/mail.info
 
to check the sendmail activity;...

Greetings

---

