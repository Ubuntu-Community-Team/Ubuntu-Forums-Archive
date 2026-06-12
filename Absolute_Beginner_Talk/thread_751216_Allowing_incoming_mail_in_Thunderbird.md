---
title: "Allowing incoming mail in Thunderbird"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by CaptainLinux94 on 2008-04-10
Hey everyone,

I'm having some problems with Thunderbird (I don't know which version I'm using...  All I know is it's the default client with 7.10 Gutsy, Ubuntu of course...).  The smtp server is fine; when I send/receive mail it shows the smtp server is done loading but the bar representing the POP's progress doesn't go past 0%.

Has anyone had a problem with this before in Thunderbird?  Note I've already enabled HTTP, HTTPS, POP3, and SMTP in Firestarter for both inbound & outbound.

Thanks,
CL94

---

### Post by munkyeetr on 2008-04-10
What mail server are you using (Yahoo, GMail, etc...)? and please post your POP setting line in the Thunderbird account.

---

### Post by CaptainLinux94 on 2008-04-10
I am using GMail.

In my policies tab under Firestarter, on both drop down selections for inbound and outbound communications you can see in the bottom most window:
**(Inbound traffic policy)**
Allow Service -    Port     -        For

HTTP                    80                everyone

HTTPS                  443              everyone

POP3                  110             everyone

SMTP                 25                everyone

IMAP                  143              everyone
[B]
    (Outbound traffic policy)[/B]
The option restrictive by default, whitelist traffic is selected.

(in the very bottom box)

Allow service     -  Port      -      For

HTTP                     80              everyone

HTTPS                  443              everyone

POP3                   110               everyone

SMTP                  25                 everyone

IMAP                    143               everyone







Hope that helps,
CL94

---

### Post by munkyeetr on 2008-04-10
I was actually asking about your Thunderbird settings. Please verify that both Gmail and Thunderbird are set up correctly for POP access.

[http://mail.google.com/support/bin/answer.py?answer=38343](http://mail.google.com/support/bin/answer.py?answer=38343)

---

### Post by Golem XIV on 2008-04-10
GMail doesn't use the standard POP3 port, it uses SSL encryption on a different port.  Can t remember which one exactly, you can go to your GMail account page and look for Thunderbird setup instructions.

---

