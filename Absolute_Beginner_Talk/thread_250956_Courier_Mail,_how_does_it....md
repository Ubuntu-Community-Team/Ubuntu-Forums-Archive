---
title: "Courier Mail, how does it..."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by wakaimono on 2006-09-04
Ok, so I am new to the world of Linux. I found the "Courier Mail server" packages in Synaptic. Unfortunately, after loading/installing, I don't know how to configure it. Help!!!

---

### Post by szf on 2006-09-04
What are you trying to do? Do you want to host mail service thru a local LAN?

---

### Post by wakaimono on 2006-09-04
Yes, currently host mail service for my domain on a Windows system. Went to the website for Courier Mail Server, but configuration instructions were not clear.

---

### Post by lupine_nickt on 2006-09-04
I've got mine set up to do mailboxes for about 6 different domains, using mysql and maildir. To be honest, Courier is a complete pain - you might be better off with Dovecot, which is trivial to set up.

If you're determined to use Courier, you might want to look [here](http://insanegenius.net/postfix.html) for the HOWTO that I used.

xF,

...Nick

---

### Post by szf on 2006-09-04
> **lupine_nickt said:**
> To be honest, Courier is a complete pain - you might be better off with Dovecot, which is trivial to set up.

I agree. The defaults for Dovecot make most configuration (busywork) unnecessary. I use a local Maildir backed by Dovecot, with fetchmail doing the pulling from my remote host.

---

