---
title: "an easy to setup console based email client?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by K3WHO on 2007-02-07
Can anyone recommend an easy to set up, console based email client I can use to check and send email on my isp account? I'd like to be able to check my email from other computers simply by sshing into my home comp. 

Thanks for any help :)

---

### Post by irish_flu on 2007-02-07
PINE is awesome!

---

### Post by K3WHO on 2007-02-07
Yeah, I have that installed but I couldn't figure out how to set it up to use my isp's incoming server. It had an entry in the setup for smtp server but I didn't see anything for pop. Am I missing something?

---

### Post by Brunellus on 2007-02-07
I'd go with mutt.  here's a setup guide:

[http://www.linux.com/article.pl?sid=06/11/30/1227239](http://www.linux.com/article.pl?sid=06/11/30/1227239)

Also:  PINE isn't free software, so I don't feel cool about recommending it.  That said, I am enormously sentimental about PINE and PICO, since I used them both all through college.  *sigh.* memories.

---

### Post by K3WHO on 2007-02-07
Okay, I gave that a shot and went through the instructions posted there and I believe I have it almost set up right. I used ssmtp and I have it sending email out to my webmail account but it's saying it came from k3who <osiris@xxxxxx.net> and it should be My Name <k3who@xxxxxx.net> I'm not sure which config file that would be covered in.

---

### Post by tbroderick on 2007-02-07
Try your .muttrc. Two lines;
```

set from="your-mailaddress"
set realname="yourname"

```

---

### Post by K3WHO on 2007-02-07
Okay I added those to .muttrc but I noticed when I went to send a message the mail from field was still left blank in mutt and I still had the same header when I sent a test mail to my webmail. It's like it's not reading my .muttrc file. When I installed mutt I noticed that there was no .muttrc file in my home dir so I created one. I thought there should have been a file there though. If this is any help, this is what I have in that file.

```

set from=k3who@xxxx.net
set realname=Jason_xxxx
set pop_user=k3who
set pop_delete=no
set pop_pass=xxxx
set pop_host=pop://pop.xxxxxx.net
set markers=no
set editor=nano
set quit=ask-yes
set sendmail=/usr/sbin/ssmtp

```

---

### Post by tbroderick on 2007-02-07
> **K3WHO said:**
> Okay I added those to .muttrc but I noticed when I went to send a message the mail from field was still left blank in mutt and I still had the same header when I sent a test mail to my webmail. 

What's your ~/.msmtprc look like. Here's mine;
```

defaults
tls on

#Gmail

account gmail
host smtp.gmail.com
from xxxx@gmail.com
auth on
user xxxx@gmail.com
password xxxxxx
port 587

account default : gmail
```

---

### Post by K3WHO on 2007-02-07
hmmm... there is no .msmtprc file in my home dir. :(

---

### Post by tbroderick on 2007-02-08
> **K3WHO said:**
> hmmm... there is no .msmtprc file in my home dir. :(

Sorry, I thought you were using msmtp. I'm not familiar with ssmtp.

---

### Post by K3WHO on 2007-02-08
np...you had be a little confused for a while though... no biggie :P

---

### Post by andrew.46 on 2007-07-05
Hi,

 There is a walkthrough targetted specifically at Ubuntu:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                       Andrew

---

### Post by andrew.46 on 2007-07-16
Hi,

 You may have sorted it out by now:

> **K3WHO said:**
> Okay, I gave that a shot and went through the instructions posted there and I believe I have it almost set up right. I used ssmtp and I have it sending email out to my webmail account but it's saying it came from k3who <osiris@xxxxxx.net> and it should be My Name <k3who@xxxxxx.net> I'm not sure which config file that would be covered in.

 but the configuration file for ssmtp is ssmtp.conf. This is usually in /etc/ssmtp/ssmtp.conf

                     Andrew

---

