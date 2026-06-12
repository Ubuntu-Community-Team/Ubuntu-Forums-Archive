---
title: "Opera Mail Setup in Evolution?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-12
Okay,


I'm trying to setup Opera WebMail in Evolution on [ubuntu (Linux)](http://www.ubuntu.com) and I can *receive* mail fine, but when I try to *send* e-mail I am told (after about 5 minutes of Evolution trying to send):
[i]Evolution Error
Error while performing operation.

Could not connect to smtpx.operamail.com: connection timed out[/i]


Here are my settings...

Account Editor-->Receiving Email
* Server Type: POP
* Server: pop3.operamail.com
* Username: *my_name*@operamail.com
* Use Secure Connection: Never
* Authentication Type: Password

Account Editor-->Sending Email
* Server Type: SMTP
* Server: smtpx.operamail.com
* Server requires authentication: *Checked*
* Use Secure Connection: Never
* Authentication Type: Login
* Username: *my_name*@operamail.com


Can anyone help?

---

### Post by CarpKing on 2006-05-12
Are you sure that that is the correct SMTP server for that account?  If it is, and it still doesn't work, you might have to use a different one.  Do you have an email account through your ISP?  Try using that SMTP.  I have multiple accounts set up through Thunderbird, but I have to switch the SMTP every time I move between college and home.

---

### Post by dcstar on 2006-05-12
[QUOTE=CybaCowboy]Okay,


I'm trying to setup Opera Mail in Evolution on Ubuntu Linux and I can *receive* mail fine, but when I try to *send* e-mail I am told:
[i]Evolution Error
Error while performing operation.

Host lookup failed: smtpx.operamail.com: name or  service not known[/i]
......[/QUOTE]

Open a terminal, type:
```
telnet smtpx.operamail.com 25
```
and see what you get.

---

### Post by CybaCowboy on 2006-05-12
The wording of my original post was slight off (the original error message was the first one I had, before I fixed a spelling error in my settings) and unfortunately, I edited my post *just* as you replied!

So yeah, you all might want to re-read my original post...


[QUOTE=dcstar]Open a terminal, type:
```
telnet smtpx.operamail.com 25
```
and see what you get.[/QUOTE]

[i]cowboy@Cowboy:~$ telnet smtpx.operamail.com 25
Trying 205.158.62.125...[/i]

That's it; nothing more, nothing less (I left it for a generous five minutes too!).

---

### Post by dcstar on 2006-05-12
[QUOTE=CybaCowboy]
.......
[i]cowboy@Cowboy:~$ telnet smtpx.operamail.com 25
Trying 205.158.62.125...[/i]

That's it; nothing more, nothing less (I left it for a generous five minutes too!).[/QUOTE]

Then you have a networking issue, as I can connect into the SMTP server with that command.

Either your ISP blocks Port 25 connections to other SMTP servers, or you are blocking them somewhere.

---

### Post by CybaCowboy on 2006-05-12
[QUOTE=dcstar]Then you have a networking issue, as I can connect into the SMTP server with that command.

Either your ISP blocks Port 25 connections to other SMTP servers, or you are blocking them somewhere.[/QUOTE]

But it works fine in Windows...

---

### Post by CybaCowboy on 2006-05-13
I e-mailed Opera Premium Mail's support and they suggested a change in the port number, but despite my best attempts, I have not been able to find where to specify an alternate port in Evolution.


Fortunately, I discovered that The GIMP can capture screen-shots, so I took a few screen-shots of my incoming/outgoing settings and forwarded them to Opera...

Evolution is a **lot** more flexible than Microsoft when it comes to authentication settings, so I'm hoping that the problem is just me selecting the wrong option.


Find the screen-shots I sent to Opera Premium Mail support below...

---

### Post by dcstar on 2006-05-13
[QUOTE=CybaCowboy]I e-mailed Opera Premium Mail's support and they suggested a change in the port number, but despite my best attempts, I have not been able to find where to specify an alternate port in Evolution.
......[/QUOTE]
Try smtp.website.com:444 (or whatever port is required).

---

### Post by CybaCowboy on 2006-05-13
Take a look for yourself...

[i]cowboy@kubuntu:~$ telnet smtpx.operamail.com 587
Trying 205.158.62.125...
Connected to pop24.pr.outblaze.com.
Escape character is '^]'.
220 pop5-1.us4.outblaze.com ESMTP[/i]

Is this any help?


To me, this means absolutely nothing, but it looks like it's doing what it's supposed to...

Of course, if it's the new port number that caused things to work, it's still kinda pointless because I can't find the port settings in Evolution!

---

### Post by CybaCowboy on 2006-05-13
I tried using Mozilla (Firefox) Thunderbird instead, which as I suspected, allowed me to change the port number to that suggested by my e-mail service provider (587 in this case)...

Everything works fine now and I'm so impressed with Thunderbird in its performance/appearance that it's highly likely I will replace Microsoft Outlook Express with it on my Windows XP install!

---

### Post by dcstar on 2006-05-13
[QUOTE=CybaCowboy]Take a look for yourself...

[i]cowboy@kubuntu:~$ telnet smtpx.operamail.com 587
Trying 205.158.62.125...
Connected to pop24.pr.outblaze.com.
Escape character is '^]'.
220 pop5-1.us4.outblaze.com ESMTP[/i]

Is this any help?


To me, this means absolutely nothing, but it looks like it's doing what it's supposed to...

Of course, if it's the new port number that caused things to work, it's still kinda pointless because I can't find the port settings in Evolution![/QUOTE]
As I posted in the previous reply:

**smtpx.operamail.com:587**

---

### Post by stuarttaylor on 2006-11-24
> **dcstar said:**
> As I posted in the previous reply:

**smtpx.operamail.com:587**

I was wondering how to specify the port number for a couple of weeks now. :rolleyes: :rolleyes:

It's so simple now when you look at it.

Thanks for that.  :D :D :D :D

---

