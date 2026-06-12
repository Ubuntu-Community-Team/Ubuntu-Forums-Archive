---
title: "Sending email works, receiving doesn't."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by napi on 2008-03-15
Hey all.

I've followed the guide for setting up postfix. All went smoothly.

So, I tried to send an email to my new server from gmail, but nothing happend.

I telnet'd to the machine (on port 25) and sent an email from there to my gmail account and that worked fine.

Then sent another mail to my server from gmail, waited a couple hours, then looked at the mail.log

There was nothing there (last entry was from couple of hours earlier when I sent the email out)

Am guessing theres a problem with DNS/MX Record stuff but not entirely sure where. MX Records for the domain are pointed to the ip of the machine (had no clue what I was doing so seemed like a good idea at the time!)

Any help is greatly appreciated.

- napi

---

### Post by dcstar on 2008-03-16
> **napi said:**
> Hey all.

I've followed the guide for setting up postfix. All went smoothly.

So, I tried to send an email to my new server from gmail, but nothing happend.

I telnet'd to the machine (on port 25) and sent an email from there to my gmail account and that worked fine.

Then sent another mail to my server from gmail, waited a couple hours, then looked at the mail.log

There was nothing there (last entry was from couple of hours earlier when I sent the email out)

Am guessing theres a problem with DNS/MX Record stuff but not entirely sure where. MX Records for the domain are pointed to the ip of the machine (had no clue what I was doing so seemed like a good idea at the time!)

Any help is greatly appreciated.

- napi

Firstly, you need a public IP address to receive e-mails, and the system must be able to be connected to by port 25 from the Internet, is this the case?

---

