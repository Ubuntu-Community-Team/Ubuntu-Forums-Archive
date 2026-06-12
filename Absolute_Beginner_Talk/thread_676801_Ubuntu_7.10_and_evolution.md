---
title: "Ubuntu 7.10 and evolution"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Paul86fxr on 2008-01-24
I Have managed to get evolution to receive e-mail but not send, I have changed the settings  and it still downloads new mail but hangs up while sending mail. I tried to detect the protocol for 'login' 'plain' etc and the server times out cant detect it from the server. any ideas? i've removed it and reinstalled and all that but have the feeling i'm missing something simple. Any help would be great.

---

### Post by Joeb454 on 2008-01-24
Well first we need to know what email you're trying to connect to :)

Otherwise we can't help :p

---

### Post by mikeyphi on 2008-01-24
> **Paul86fxr said:**
> I Have managed to get evolution to receive e-mail but not send.

I agree with post #2 
however, meanwhile confirm your settings:
sending email is usually (but not always) done through SMPT whilst receiving is via POP
you might also need to check the 'server requires authentication' box and the 'remember password' box

---

### Post by Paul86fxr on 2008-01-24
I've tried my yahoo account and my millenicom account;  POP.millenicom.com and smtp.millenicom.com, I went to their website and verified the information, same with yahoo. I am missing something. I hope this answers your question but i'm starting to doubt everything. Thanks in advance.

Paul

---

### Post by Paul86fxr on 2008-01-24
My mail server asks me to enable 'SMTP authorization" with is not an option on evolution, at least not with those exact words.

---

### Post by Michl on 2008-01-24
You need an outgoing smtp server.   You must use the smpt server of your ISP (if they
let you, etc.) or use a VPN connection to your email provider and use their outgoing
network server.  A third option is to subscribe to an outgoing server available online.

But it is a good idea to use the same smtp servers for outgoing and
incoming mail because Barracuda, for example, blovks mail with distinct incoming and
outgoing servers.  

Michl

---

### Post by Paul86fxr on 2008-01-25
I'm starting to think that there is a bug in my edition of evolution, I configured thunderbird the same way and its working great, at this point I have no idea but thaks for the help.

Paul

---

### Post by dcstar on 2008-01-25
> **Paul86fxr said:**
> My mail server asks me to enable 'SMTP authorization" with is not an option on evolution, at least not with those exact words.

Yes it is, it is there in Edit-Preferences-Mail Accounts-Sending Email "Server requires authentication".

---

### Post by Paul86fxr on 2008-01-26
David, I tried that as well,  I think i'm going to completely remove it and start again.  it makes no sense. Its straight forward. Thanks for the suggestion, I will keep trying.

Paul

---

