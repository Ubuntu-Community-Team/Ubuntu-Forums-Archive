---
title: "Migration from FreeBSD to Ubuntu Server (password issues)"
date: 2008-04-28
forum: BSD
---

### Post by growlf on 2008-04-28
For various reasons, a client of mine is moving from FreeBSD to Ubuntu Server.  They have FreeBSD 6.0-RELEASE-p6 currently and we are loading Ubuntu Gutsy Server for the new boxes.  

All has gone well as far as the retraining of the IT personelle for using and maintaining Ubuntu (I tend to like it better myself as well - which makes this easier) and package availability/installation.  However, we seem to have run into a snag when it comes to migrating the accounts themselves.  Specifically the passwords - we don't want to do a forced reset of all account passwords and would rather do this as seamlessly in the user's perspective as possible.

Is there an easy way to simply migrate the password db over intact and have Ubuntu use it temporarily, or to import it directly into it's own hash? 

I have looked across the web as well as searched these forums for "migration" topics regarding BSD and Ubuntu - no luck.  I am hoping one of you fine guru's here will have a suggestion to get me over this hurdle.

Thanks in advance.

---

### Post by mips on 2008-04-29
Unless you are using something like ldap this might just end up being a manual procedure. Migrating from linux to fb is pretty simple though.

Look at utils like awk, unshadow etc

[http://www.freebsd.org/cgi/man.cgi?query=passwd&apropos=0&sektion=0&manpath=FreeBSD+6.0-RELEASE&format=html](http://www.freebsd.org/cgi/man.cgi?query=passwd&apropos=0&sektion=0&manpath=FreeBSD+6.0-RELEASE&format=html)
[http://www.gnu.org/manual/gawk/html_node/Passwd-Functions.html](http://www.gnu.org/manual/gawk/html_node/Passwd-Functions.html)

I'm a bit weary of posting more links as I might end up running foul of forum rules risking infractions. So my suggestion to you is to google and maybe wander on over to the darker side of the internet.

To make your life easier in future look into LDAP/Kerberos etc.

---

