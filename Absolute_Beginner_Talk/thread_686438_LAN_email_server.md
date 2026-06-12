---
title: "LAN email server"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-02-03
My LAN has a number of Win98, some WinXP and one Ubuntu desktops. I want to setup an internal email network. I have setup something similar on an XP computer using MailEnable but now I want to do this in Ubuntu.
Our company website is (say xyz.com). It has number of email id's, say info, admin (@xyz.com). Some computers on the LAN are having internet access and are using these email addresses to send and receive outside mails.
I want to setup my internal domain to also as xyz.com. All the LAN computers will be given some email address, say purchase, production etc (@xyz.com).
The LAN computers should be able to send and receive internal messeges through my Ubuntu desktop, without needing internet connection.
But I also want them to be able to send messeges to outside the LAN, through my Ubuntu desktop. But in this case, the mail should go as having an id present on my website, say [email]admin@xyz.com[/email]. For this I think I need an SMTP server or something. I want to be able to use my website SMTP settings for this.
I hope I am not confusing. In short, if a user sends a mail to an internal user, it should go to the user directly and if to an outside address, then it should use the SMTP settings of my website.
As I said, I have setup the internal thing using MailEnable on an XP computer and created accounts in each computer in OE and it is working. But I was not able to send outside mails properly. Now I want to do all this in Ubuntu. Is it possible easily?

---

### Post by jrothwell97 on 2008-02-03
All you should have to install is an IMAP server, or perhaps a POP3 server. I recommend IMAP, as it is more secure and will keep the Email folders in sync across the machines.

Ubuntu Server allows you to install these at installation - otherwise you can install them with Synaptic.

---

### Post by jesrani on 2008-02-03
I dont really know what IMAP is but I just want to send mails from Outlook Express in one machine to Outlook Express in another machine. And allow some machines (without internet) to send email from Outlook Express to an outside email address.
I dont want anything web-based and having all mails on the Ubuntu machine.

---

### Post by jesrani on 2008-02-03
Can anyone help me please. I have changed my requirements a bit. My Ubuntu machine has an IP address 192.168.1.1. It is connected to other Win98 machines.
All I want to now is to setup an email account (in Outlook Express) on the 98/XP machines (which dont have internet) for outgoing mails. The outgoing server should be 192.168.1.1 and these mails should be sent to any outside email address through my Ubuntu machine. I would like to use my website SMTP settings for doing this, is it possible????

---

