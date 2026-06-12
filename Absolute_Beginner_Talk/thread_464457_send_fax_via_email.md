---
title: "send fax via email"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-06-04
n00be - needing help please!

Question #1:

I want to be-able to send fax via email.

I understand that the courier-faxmail program will do
just that. It's the only program I've been able to find
that can send fax by email.

But, my ISP (dialup frys.com) has WebMail only(no pop mail).

My question is: will I be able to send fax without
using pop mail I will be using kmail?

Or,is that what the courier-mta "Courier Mail Server
and faxmail gateway" is used for? I'm just guessing!

I have not been able to find much help if any at all
on just how courier-faxmail works, I'm still searching.

If courier-faxmail requires pop mail only, then I
wont be able to use courier-faxmail.

Question #2:
Where can I find "HELP, INFO, READ-ME information" on
courier-faxmail? I've googled & yahooed for a week now
with very, very little results.

Thank you for taking the time to look at my request.



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Heres the courier-faxmail packages that synaptic will
install on my Mepis 6.0, kde system:

~~~~

  courier-faxmail (version 0.47-13ubuntu5)
  Courier Mail Server - Faxmail gateway
  The courierfax module implements a faxmail gateway, which faxes a printed
  copy of an email message to the phone number specified in the email address
  (e.g. 5558888@fax).

~~~~

  courier-authdaemon (version 0.47-13ubuntu5.1)
  Courier Mail Server - Authentication daemon
  This package contains the authentication daemon for the
  Courier Mail Server.

~~~~ 
  courier-base (version 0.47-13ubuntu5.1)
  Courier Mail Server - Base system
  The Courier mail transfer agent (MTA) is an integrated mail/groupware
  server based on open commodity protocols, such as ESMTP, IMAP, POP3, LDAP,
  SSL, and HTTP. Courier provides ESMTP, IMAP, POP3, webmail, and mailing list
  services within a single, consistent, framework.
  
  This package provides the functionality needed by all Debian courier packages
  like some configuration files, helper programs and the Courier TCP server
  daemon.

~~~~

  courier-mta (version 0.47-13ubuntu5)
  Courier Mail Server - ESMTP daemon
  This ESMTP daemon uses an efficient maildir format as its native storage
  format, supports IPv6, implements SMTP extensions for mailing list
  management and features integrated mail filtering. It can function as an
  intermediate mail relay, relaying mail between an internal LAN and the
  Internet, or perform final delivery to mailboxes.

~~~~

  mgetty (version 1.1.33-3ubuntu2)
  Smart Modem getty replacement
  Mgetty is a versatile program to handle all aspects of a modem under Unix.
  
  The program 'mgetty' allows you to use a modem for handling external
  logins, receiving faxes and using the modem as a answering machine without
  interfering with outgoing calls.
  
  This package includes basic modem data capabilities. Install mgetty-fax to
  get the additional functionality for fax. Install mgetty-voice to get the
  functionality to operate voice modems.
  
  Mgetty is also configurable to select programs other than login for special
  connections (eg: uucico, fido or other programs) depending on the login
  userid. It also supports caller-id if the modem and phone line supply it,
  and can deny connections based on originating telephone number.
~~~~
  mgetty-fax (version 1.1.33-3ubuntu2)
  Faxing tools for mgetty
  The fax subsystem of the mgetty package.
  
  This subsystems has the enhancements that are needed to send and receive
  faxes with mgetty and a Class 2 faxmodem.
  
  The program 'mgetty' allows you to use a fax modem for receiving faxes
  and handling external logins without interfering with outgoing calls.

---

### Post by pkarjala on 2007-06-04
A quick google search didn't reveal much in the way of a manual for courier-faxmail.

However, in regards to setting up your email, your ISP should have an outgoing mail server of some sort.  Try contacting them directly to see if there's anything of the type.  If they really don't, you'll need to find a different mail server to route through.

---

### Post by housekid on 2007-06-04
Thanks - pkarjala
Thats the killer answer I didn't want to hear!

Thanks for helping me out.

---

