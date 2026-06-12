---
title: "I know its more to it..."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2006-12-28
I configured proftp as an INETD server as opposed to a standalone server. I want to reconfigure the proftp server into a standalone server. Using webmin, I edited the proftp.conf 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

I'm sure there is more to it than that change in text;) 

Thanks again
Kirk

---

