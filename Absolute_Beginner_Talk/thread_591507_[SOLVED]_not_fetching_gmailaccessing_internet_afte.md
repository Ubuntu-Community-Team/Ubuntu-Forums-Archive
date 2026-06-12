---
title: "[SOLVED] not fetching gmail/accessing internet after setting rules in Firestarter"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by offline on 2007-10-25
Following instructions of some widely publicized book I set these rules:

_Inbound:_

BitTorrent

_Outbound:_

HTTP
HTTPS
POP3
BitTorrent
SMTP

Earlier I enabled Evolution to fetch mail from GMail successfully and had internet access(with the firestarter running without user defined rules).

What am I doing wrong here?

---

### Post by MegaJim on 2007-10-25
The simple way to do this is to review the firestarter logs when you make a connection attempt; it will let you know which packets were blocked including port number, time and direction (hint: its in the firestarter UI, under 'Events')

If there are no events, first check your iNet connection is functioning properly by pinging [www.google.com](www.google.com) or [www.microsoft.com](www.microsoft.com)

If you don't have connectivity you might need to enable ICMP traffic for a DNS to be configured properly

[QUOTE=Gmail Help Pages]Incoming Mail (POP3) Server - requires SSL:	pop.gmail.com
Use SSL: Yes
Port: 995 
Outgoing Mail (SMTP) Server - requires TLS:	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587 
Account Name: 	your Gmail username (including @gmail.com) 
Email Address: 	your full Gmail email address (username@gmail.com) 
Password: 	your Gmail password[/QUOTE]

---

### Post by offline on 2007-10-25
> **MegaJim said:**
> The simple way to do this is to review the firestarter logs when you make a connection attempt; it will let you know which packets were blocked including port number, time and direction (hint: its in the firestarter UI, under 'Events')

OK I can browse websites but no email:

[COLOR="Red"]TERMINAL OUTPUT AFTER TRYING TO FETCH GMAIL MAIL FROM EVOLUTION[/COLOR]

```
:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:15250): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:15250): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:15250): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:15250): DEBUG: mailto URL program: evolution
process 15250: The last reference on a connection was dropped without closing the connection. This is a bug in an application. See dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.
```

[COLOR="Red"]FIRESTARTER blocked events after trying to fetch gmail mail with evolution:[/COLOR]

```
Port 995  - -source 10.0.0.7 --protocol TCP-- service pop3s
```

Whenever I remove rules evolution connects to gmail.

---

### Post by MegaJim on 2007-10-25
From that log, it seems you need to create a new outgoing rule to allow UDP traffic on port 995

---

### Post by offline on 2007-10-25
Thanks MegaJim, it worked.

I typed UDP  and port no 995 at outgoing rules and the firewall changed this to Pop3s very nicely. I hope opening up 995 for pop3s is not a security risk however

---

### Post by MegaJim on 2007-10-25
You are welcome

---

### Post by dwardingley on 2008-01-24
I know that the pop3 protocol sends out your login details as plaintext.

If I set up Evolution to connect to pop.gmail.com:995 and smtp.gmail.com:465, does that mean that I am automatically connecting using pop3s?

And by extension, does it mean that my logins are _not_ being sent as plaintext and that it is "safe" to use a public wifi point to collect email?

(Have googled this, and can't seem to find a clear answer, which I accept might be a reflection on my google skills...).

Would appreciate a reply, thanks.

D.

---

### Post by MegaJim on 2008-01-24
There is no simple way to know how evolution will behave.  Perhaps doing a little experiment at home with wireshark will get you the answers you seek.

---

### Post by LeAstrale on 2008-01-24
please make a note in the thread here if you do find out about the plaintext thingy. 

Thanks

/Astral-1

---

