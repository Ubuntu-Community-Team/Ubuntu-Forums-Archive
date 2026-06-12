---
title: "Cant get Evolution to send mail"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Norman Thom on 2006-09-01
Help!  using Dapper, can't send email.  Seems to fetch incoming mail but the send function just sits there 'til I cancel it.

Set up stuff:

In Identity:

Entered full name
entered email address(prefix@<ISP>.ca)

In Receiving email:

Set server type to POP

Entered Server pophm.<ISP>.ca

Entered Username:  Full email address

set security to SSL

checked remember password

In Sending email:

Entered server smtphm.<ISP>.ca

checked server requires authentication

Entered username

Told software to forget password

sent a leter

Entered passowrd

checked remember password

POP server seemed to function

SMTP just sat there

Canceled action for SMTP

set profile to remember password and tried again . . . same thing

Does anyone have any ideas

---

### Post by DSn0wMan on 2006-09-01
I forget exactly what it was, but it seemed that my ISP's smtp server used different authentication methods then the default.

I was able to have Evolution test the authentication type, then use the type it recommended.

In the configuration GUI when you get to the Sending Email page uder Authentication there is a button that says "Check for Supported Types". Clik it to find the proper authentication type.

This cured the no SMTP thing.

---

### Post by clesage on 2006-09-01
Hi Norman. I am having the exact same trouble. The problem is, my ISP doesn't reply to "Check for Supported [Authentication] Types". Also I have tried them all, and none of them work anyway.

Also I have tried my website's SMTP and even my work's SMTP, and they all do the same thing. So I figure it **must** be a problem on my end.

There is another thread that I saw, where someone suggested this may be a DNS problem. That Ubuntu autodetected (I think) an inappropriate DNS server that his ISP isn't using, and so port 25was blocked.

Anyone: Does that sound feasible? What would I ask my ISP for if I wanted to "update my DNS"?

---

### Post by gn2 on 2006-09-01
Have you tried without authentication?

---

### Post by Nytram on 2006-09-01
Evolution seems to require SMTP authentication by default, but I was able to get mine working by turning it off.

---

### Post by Norman Thom on 2006-09-01
Tried without authentication, no go

---

### Post by Nytram on 2006-09-01
Are you sure you have the correct address of your SMTP server? Every ISP I've been with uses smtp.<ISP> whereas you're using smtphm.<ISP>

Otherwise, im stuck for an answer..

---

### Post by Norman Thom on 2006-09-01
My ISP has me include th 'hm ' in the SMTP address

---

### Post by Norman Thom on 2006-09-01
BTW  I successfully set up evolution to send and receive mail about 2 days ago on another computer using these settings.  I just don't understand and no longer have access to that computer

---

### Post by Norman Thom on 2006-09-01
Quite suddenly it seemed that the SMTP server was being queried.
After another couple of minutes got an error: 'could not connect to smtp . . . connection timed out

---

### Post by gn2 on 2006-09-01
Could it be a firewall issue, and have you checked with ISP that all is well at their end? 
Have you tried re-installing Evolution packages with Synaptic?

---

### Post by Ms Dainty on 2006-09-01
I noticed you're in Ontario: is Rogers your ISP? If so, you may be the victim of their SMTP policy. See

[http://www.rogershelp.com/yahoo/mail/smtp.html](http://www.rogershelp.com/yahoo/mail/smtp.html)

---

### Post by chromewarrior on 2006-10-15
I cant send out any thing it says --- broken pipes wtf is a broken pipe on a pc ???????????

---

### Post by ramjet_1953 on 2006-10-15
I found with Yahoo they require TLS encryption . Maybe you need to try this, also

Roger

---

### Post by nevernamed on 2007-03-17
I'm having a similar problem except that I can receive mail from imap server, but for some reason I can't send.
I get the error:
Error Unable to send message, Reason Broken Pipe.

I have no idea what this means. Any help would be great, Thanks.

---

### Post by croxi on 2007-04-28
I'm having no success in making Evolution send my emails, it says each time that I have a broken pipe and that when I tried to install the evolution software again, it doesn't make a blind bit of difference, I still have that damned broken pipe.

---

### Post by DSn0wMan on 2007-04-28
Try downloading thunderbird 2. It is an awsome email client, and has lots of usefull extensions.

---

### Post by croxi on 2007-04-30
I've been trying to get Evolution to send my emails, but there's this broken pipe, I tried to follow advice about installing Thunderbird 2 but installing that and its not allowing me to install the program, maybe I'm going about installation of such things in a MSWin fashion, expecting it to be a little easier, but its not, its harder to install when I'm not familiar with how to install programs with UBUNTU 7.06 compared to  Windoze. 

I just want to fix the damned broken pipe and get those damned emails out. any help would be greatly appreciated. 

any help would be great.

---

### Post by graigsmith on 2007-04-30
the server may not require authentication. i had to disable that setting, then mine worked.

---

### Post by DSn0wMan on 2007-04-30
If you still want to install Thunderbird 2 you can install it with a script located here - [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)

If you want to install Thunderbird 1.5 ```
sudo aptitude install mozilla-thunderbird
``` or just select it from Applications -> add / remove program

---

### Post by sailor2001 on 2007-04-30
a pipe is your dsl modem....... check with your isp for replacement

---

### Post by croxi on 2007-05-02
ok, so the broken pipe is the Modems fault, guess who's going in the bin then...well, I still don't get any success with getting hotmail on my laptop no matter how hard I stare hard at it. 

I have tried the following:-

sudo apt-get update
sudo apt-get install inetutils-inetd
sudo apt-get install hotway hotsmtp
sudo gedit /etc/inetd.conf
pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd
2500 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd
sudo /etc/init.d/inetutils-inetd restart

restart internet superserver inetd   [ok]

then I went through the normal config but I´m not sure that the IP address is right for me, but I could be wrong, its set as 127.0.0.1

---

