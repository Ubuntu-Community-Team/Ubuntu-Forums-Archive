---
title: "How does an e-mail server work?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-10-18
I've been trying to get my ubuntu server able to send e-mail messages, but I have no idea how it works. The documentation here didn't explain much. I called godaddy who I registered my domain with and they said "your own server?" we can't help you with that...

If you have any advice, let me know:)

---

### Post by steveneddy on 2007-10-18
Maybe posting in the Servers and Securities forums would help you better.

---

### Post by yabbadabbadont on 2007-10-18
However, don't just start a duplicate thread in that forum.  Report your first post and ask a mod to move the thread for you.  :)

As for advice on your problem, you haven't provided any information at all about what software you have installed, how you configured it (or didn't), what you have tried to fix the issue, and what error messages/behavior you see.  Without information like that, no one will be able to help you.

---

### Post by Xarok on 2007-10-18
> **steveneddy said:**
> Maybe posting in the Servers and Securities forums would help you better.

I posted there first, and I'm not getting much advice.
This forum is more active and I *am* an absolute beginner to this e-mail thing.

> **yabbadabbadont said:**
> However, don't just start a duplicate thread in that forum.  Report your first post and ask a mod to move the thread for you.  :)

As for advice on your problem, you haven't provided any information at all about what software you have installed, how you configured it (or didn't), what you have tried to fix the issue, and what error messages/behavior you see.  Without information like that, no one will be able to help you.

I just want general advise. Because I have *no concepte *of how mail works.

So you wnat more info...

I have Ubuntu LTS 6.06 server
and I follow these instructions here for e-mail services:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)
when it says replace mail.example.com with your e-mail host I have no idea what that means. My domain name that directs to my server I assumed. When I did that it didn't work. When I used the server's local host name it seamed to work though, when I did the telnet command (what ever that does...).

Someone in the other forum said I needed to use my actual domain name... and said i needed it to resolve forwards and backwards (whatever that means...)

See, I am a damned noob. This thread belongs here :)

---

### Post by steveneddy on 2007-10-18
If you are behind a router, do you have the mail ports open?

---

### Post by Technoviking on 2007-10-18
This article has some info,
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by llamakc on 2007-10-18
And have you set an MX record to point to your servername?

---

### Post by Xarok on 2007-10-18
> **steveneddy said:**
> If you are behind a router, do you have the mail ports open?

Yes I am behind a router.
Do you mean port forwarding for the mail ports? What is the e-mail port? 2222?
Do I set port forwarding for this?

> **llamakc said:**
> And have you set an MX record to point to your servername?
You mean, do I have the MX records (in my godaddy account) to direct to the IP with my server.
I tried that, but I don't know what I'm doing...

---

### Post by steveneddy on 2007-10-18
> **llamakc said:**
> And have you set an MX record to point to your servername?

AH - I forgot about that one.

---

### Post by HermanAB on 2007-10-18
Hmm, installing a mail server can be very difficult, but it doesn't have to be difficult - it is entirely your choice whether you wish to follow the hard or easy route!

The mail system is disjunct, which makes it complex:
1. SMTP MTA (Postfix, Qmail) send and receive email to/from other MTA on port 25.  Received mail gets plonked into a spool directory and usually either in maildirs or mailboxes.
2. POP/IMAP server (pop3d, qpopper, dovecot) provides mail to client programs (Thunderbird, Eudora, Outlook) over ports 110 or 143.
3. Mail scanners (Spam Assassin, ClamAV) sits in between things and reads your spam on your behalf, so you don't have to.
4. All of the above can also be done encrypted with SSL.
5. Authentication adds more complexity.
6. Webmail requires a web server for yet more complexity.

The most difficult mail system to install is Sendmail.  An intermediately difficult system to install is Postfix or Qmail, but Postfix/Qmail is only a small part of the story (see points 2 to 6 above).  A very easy and far superior system is Citadel, which covers points 1 to 6 inclusive in one go.

I suggest that you install Citadel: [http://www.citadel.org](http://www.citadel.org) and start playing.  It only takes about 20 minutes.  Installing any other system will take a newbe anywhere between 2 weeks and 6 months depending on where between points 1 and 6 above you give up...

Here is an older guide: [http://www.aeronetworks.ca/citadel-howto.html](http://www.aeronetworks.ca/citadel-howto.html)
(It is even easier now)

Cheers,

Herman

---

### Post by Xarok on 2007-10-18
> **HermanAB said:**
> Installing any other system will take a newbe anywhere between 2 weeks and 6 months depending on where between points 1 and 6 above you give up...

lol!

Well I'm trying to get my Joomla system to send mail, and its mail configuration options are 
- PHP mail function
- sendmail
&
- SMTP

Would Cidadel work for one of these?

---

### Post by llamakc on 2007-10-18
Tell it to do sendmail and then install mailx

sudo apt-get install mailx

---

### Post by Xarok on 2007-10-18
> **HermanAB said:**
> 

Cheers,

Herman

If you want to pretend you're from the Wild West you can't say "cheers". We don't say that here. :)

> **llamakc said:**
> Tell it to do sendmail and then install mailx

sudo apt-get install mailx

Have you used Joomla with this before?

If asks for these other fields to be filled out...

Mail From:	
From Name:	
Sendmail Path:

---

### Post by Xarok on 2007-10-18
> **llamakc said:**
> Tell it to do sendmail and then install mailx

sudo apt-get install mailx

Ok, done...
Still doesn't work V_V

---

