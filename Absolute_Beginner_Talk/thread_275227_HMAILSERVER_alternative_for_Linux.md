---
title: "HMAILSERVER alternative for Linux"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by 3zero2 on 2006-10-11
Hi all,

I'm currently using hmailserver on a windows machine but wish to switch over to ubuntu.

is there anything like hmailserver for linux?

(HMailserver is an email server, with a mysql backend, configured entirely through GUI)

thanks

---

### Post by hw-tph on 2006-10-11
There are several very competent email servers for Linux - Postfix, sendmail, exim...the list goes on. I imagine all can be used with a MySQL backend - I know for sure Postfix does (read Gentoo's excellent [Virtual mailhosting howto](http://www.gentoo.org/doc/en/virt-mail-howto.xml)). Just pick one. You will not find a full featured GUI to control the email server completely, although tools like [Webmin](http://www.webmin.com) can lighten the burden of day-to-day administration somewhat. I don't find the lack of a powerful GUI particularily disturbing - setting up a mail server might be tricky the first time but then it's up and running and adding users isn't usually too much of a hazzle. And by the way - who uses a GUI on a server? :P


Håkan

---

### Post by thomasjohansen on 2007-07-06
Hi I have also experimented with Hmailserver for windows, but now I want to make a Ubuntu server hosting Intranet and a mailserver. For the mailserver I just tried Zimbra, but i cant find a option that Hmailserver has.

I want to keep my current external webhotel mailserver and just use my mailserver to download all the mail from those to my mailserver and deligate to each individual mail account. (this is to have the internal mail, calendar and contacts in house)

In Hmailserver i could setup an external mailaccount for each account.

Is this possible in any mailserver for ubuntu, maybe even in Zimbra?

---

