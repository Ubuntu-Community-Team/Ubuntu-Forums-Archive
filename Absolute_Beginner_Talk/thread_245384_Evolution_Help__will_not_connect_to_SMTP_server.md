---
title: "Evolution Help : will not connect to SMTP server"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by samsappleton on 2006-08-27
Hi

I am beginning to use evolution - i can receive email fine from
my provider, but following their directions for sending using SMTP
I always get "Connection refused" for the SMTP server.

the provider is hyperstreet.com, smtp.hyperstreet.com:1025 with 
authentication required, PLAIN type.

The provider says they can connect fine using another application - thunderbird I think - but I like evolution more.

Any hints about how I can debug this problem?

Sam Appleton

---

### Post by toasted on 2006-08-27
Make sure the box labeled 'Server requires authentication' is ticked
Double check username and password 
Should work, its no different that Thunderbird, outlook or outlook express

---

### Post by George W. Tush on 2006-10-14
Certainly it was my understanding that it was no different than the other clients in this respect, but I'm having the same or similar difficulty samsappleton reported.

[INDENT]Unable to authenticate to SMTP server.[/INDENT]
[INDENT]Bad authentication response from server.[/INDENT]

[INDENT]Please enter the SMTP password for xxxx on host smtpauth.earthlink.net[/INDENT]

---

### Post by Coburn on 2007-02-01
It doesn't matter whether you use Evolution or Thunderbird.  I have tried both and get the same error when I try to relay mail through my webmail (an Outblaze.com server).  "Connection refused."

I have tried changing every setting in Preferences > Sending Mail and nothing seems to work.

Thunderbird with Hotway did the same thing before.

Maybe it is that they do not want anybody spamming through their server, so they make you login online first.  But I would think the setting "POP before SMTP" would fix that.  Or "Login."

---

### Post by dcstar on 2007-02-01
> **samsappleton said:**
> Hi

I am beginning to use evolution - i can receive email fine from
my provider, but following their directions for sending using SMTP
I always get "Connection refused" for the SMTP server.

the provider is hyperstreet.com, smtp.hyperstreet.com:1025 with 
authentication required, PLAIN type.

The provider says they can connect fine using another application - thunderbird I think - but I like evolution more.

Any hints about how I can debug this problem?

Sam Appleton

If you want to debug basic connectivity, do:
```
telnet smtp.hyperstreet.com 1025
```
and the resulting output will tell you if this SMTP server will accept a connection from your IP address.

If it don't, then it won't matter what client you try to use!

---

### Post by John Kemp on 2007-05-30
> **Coburn said:**
> It doesn't matter whether you use Evolution or Thunderbird.  I have tried both and get the same error when I try to relay mail through my webmail (an Outblaze.com server).  "Connection refused."

I have tried changing every setting in Preferences > Sending Mail and nothing seems to work.

Thunderbird with Hotway did the same thing before.

Maybe it is that they do not want anybody spamming through their server, so they make you login online first.  But I would think the setting "POP before SMTP" would fix that.  Or "Login."

MANY THANKS,Coburn! "Pop beforeSMPT" solved the problem for me - I'm on wires-only Metronet (PAYG Broadband) in the UK. All fine now! - John Kemp:D

---

