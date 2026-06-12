---
title: "Evolution TLS support problem"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by pillu on 2007-05-12
Hi all,

I am trying to set up evolution for my email. I can receive messages correctly (using IMAP) but have some problem with sending emails. My email server uses SMTP with TLS encryption. When I enable this option in evolution I get the following error message
> Error while performing operation.

Failed to connect to SMTP server smtp.umn.edu in secure mode: STARTTLS not supported

The send works perfectly if I turn off the encryption and I know that TLS is supported by my server. I think the problem is that the smtp server uses a non-standard port for TLS (Port #587) while evolution sends tries to send it over some other port. Can anyone help me with this?

Thanks a lot
pillu

---

### Post by pillu on 2007-05-12
I was helped out on the evolution irc channel (irc.gaim.org #evolution)....To change to a non standard port in evolution just add the port after your smtp server address after a colon. For example to connect to smtp.xyz.edu on port 123 use
> smtp.xyz.edu:123

that solved the problem

thanks
pillu

---

### Post by larytet on 2008-05-10
port 587 for SMTP with TLS in my case too
Evolution uses different port by default.

---

