---
title: "Configuring a Mail Server for Spooling mail"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by vandermerwe on 2007-02-22
Greetings,

I have been given the task of setting up a Mail Server to spool mail for users on the LAN. The primary mail server resides at our ISP. I would like to use Postfix as a MTA. I am very new to Ubuntu and I would like some assistance in the configuration process of Postfix on Ubuntu. There are at least three (3) domains that need to be catered for. The secondary mail server will periodically download mail from the primary mail server.

Any assistance will be greatly appreciated.

Yours in promoting Ubuntu to the masses.

---

### Post by kidders on 2007-02-22
Hi there and welcome,

I treat Postfix on Ubuntu identically to any other distro, really. Have you run into something weird?

---

### Post by vandermerwe on 2007-02-23
Hi, thanks for your reply,

My Mail is not being collected from the primary mail server at my ISP. I am looking at installing Zimbra just to see how it works.

Have you run into this problem before.

---

### Post by kidders on 2007-02-23
> **vandermerwe said:**
> My Mail is not being collected from the primary mail server at my ISP.Postfix won't do that for you ... it's an SMTP server. You'll need something like Fetchmail to retrieve messages from other hosts.

I don't know anything about Zimbra, I'm afraid :-(

---

### Post by vandermerwe on 2007-02-23
Thanks for your assistance. I'll let you know how it goes.

---

