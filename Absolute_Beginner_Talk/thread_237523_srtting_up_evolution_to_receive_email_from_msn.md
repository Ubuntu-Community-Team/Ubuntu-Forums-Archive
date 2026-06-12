---
title: "srtting up evolution to receive email from msn"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by unisol on 2006-08-16
im kinda stumped when it comes to setting up evoultion to receive email from msn.com i selected pop to recieve and smtp to send but pop stalls then says it cant find server could use some help i dont think im putting the server in right is it pop.msn.com or pop .hotmail.msn.com or what excuse my ignorance  but im just stumped

---

### Post by foolsh on 2006-08-16
check out this articial [http://linux.cudeso.be/linuxdoc/gotmail.php]("http://linux.cudeso.be/linuxdoc/gotmail.php")
i use this and fetchyahoo to deliver my mail to my isp's email account, it uses pop and smtp 
i then set up a cron job to check the mail every thirty minutes or so but i use kmail to check my isp's account every 5 since it is now my main email account

---

### Post by unisol on 2006-08-17
i found the solution:ode:
sudo apt-get update
Now, install the inet daemon


Code:
sudo apt-get install inetutils-inetd
This takes care of all of our dependencies. Now on to the good stuff...


Code:
sudo apt-get install hotway hotsmtp
This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.


Code:
sudo gedit /etc/inetd.conf
Look for a line like this:


Code:
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:


Code:
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
And we also need to add a line to get hotsmtpd working, just paste this at the bottom:


Code:
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:


Code:
sudo /etc/init.d/inetutils-inetd restart
If everything is working properly, you'll see this pop up on your screen:


Code:
* Restarting internet superserver inetd                            [ ok ]
Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)
thanks for your help
-------------------------------

---

### Post by b_martinez on 2006-08-17
thanks for the info, this is the 1st time it ever made sense to me.
Bill

---

### Post by unisol on 2006-08-18
im glad to know that i could help someone as much help as i needed in the past im a slow learner but catching on

---

### Post by soutSA on 2006-08-18
Anybody got the same error:

[HTML]Error sending password: -ERR Hotmail said you must pay money to have WebDAV access
[/HTML]

haha...that is microsoft for you;)

---

### Post by Pragmatist on 2006-08-24
> **soutSA said:**
> Anybody got the same error:

[html]Error sending password: -ERR Hotmail said you must pay money to have WebDAV access
[/html] 

haha...that is microsoft for you;)

I go this exact error after following unisol's directions.  

Unisol, do you pay for your hotmail account?

---

### Post by Pragmatist on 2006-08-24
> **Pragmatist said:**
> I go this exact error after following unisol's directions.  

Unisol, do you pay for your hotmail account?

Using pop3hot.com  in place of 127.0.0.1 worked for me.  I got the idea from this thread:

[http://www.ubuntuforums.org/showthread.php?t=200408&highlight=evolution+hotmail](http://www.ubuntuforums.org/showthread.php?t=200408&highlight=evolution+hotmail)

[Post #8 by **unique**]

---

### Post by cibara on 2006-10-21
Excellent how-to Unisol. It works great! Many thanks! Note that you must follow the instructions exactly, and if you do not get the daemon restart message you did something wrong. 127.0.0.1 is the mail daemon on your machine.

Thanks again!

---

### Post by jha0 on 2006-12-17
> Using pop3hot.com  in place of 127.0.0.1 worked for me.  I got the idea from this thread:I've tried that but it seems to be obsolete already. Instead, I got a com generated mail from izymail.com stating this issue. This is what I get:

>     Dear prospective user of IzyMail,

Your email application has just queried the IzyMail system and requested to
download messages for your account. However, it was detected that your email
address is not registered with IzyMail and the system cannot proceed.

You may have used the server name 'pop3hot.com' which is an earlier,
obsolete name for the same service. 


IzyMail now requires a free registration before it enables access to your
account. Registration is free of charge and the online registration form is
available at

    [http://v3.izymail.com/register.aspx](http://v3.izymail.com/register.aspx)

We thank you for your confidence in IzyMail and hope to see you back very
soon.


We hope you found this information helpful,
Have a very pleasant day,

    the IzyMail support team As for unisol's guide, it works for me too! Thanks unisol, however, just to benefit everyone, there are some updates I like to make on unisol's guide.

...
**NOTE: Only receive and send server type need to be change. The above installation procedure remains the same as follow.**
Receive Server type: POP
Server: in.izymail.com **<--- changes NOTE: You have to register with izymail.com in order to work: **[http://v3.izymail.com/register.aspx](http://v3.izymail.com/register.aspx)
Username: [EMAIL="xxx@hotmail.com"]xxx@hotmail.com[/EMAIL] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: out.izymail.com:2500 **<--- changes NOTE: You have to register with izymail.com in order to work: **[http://v3.izymail.com/register.aspx](http://v3.izymail.com/register.aspx)
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [EMAIL="xxx@hotmail.com"]xxx@hotmail.com[/EMAIL] (same as above)
(Optional Remember password checkbox)

That's all. But if anyone out there have alternative solutions, please kindly share.:D:D:D

---

