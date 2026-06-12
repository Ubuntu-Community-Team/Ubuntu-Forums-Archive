---
title: "php not working"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by djearwig on 2007-03-29
So suddenly my server won't display php scripts.  I checked the *apache2.conf* file and the *mods-enabled file*; php5 is listed in both.  After checking, I did a force reload on apache2 and still no luck.  I did a *a2enmod php5* and still no go.

Any suggestions of what else to check/do?

Thanks very much for the help...

---

### Post by jenhsun on 2007-03-29
Are you sure your modem firmware is updated?
Take a look at this thread that I had similar problem as you weeks ago.
[http://ubuntuforums.org/showthread.php?t=385279](http://ubuntuforums.org/showthread.php?t=385279)

I am a newbie LOL

---

### Post by djearwig on 2007-03-29
jenhsun - I am a noob as well, so I will take no offense to anything you say.  In fact, since you had the same problem, I am going to follow your suggestion right now.  I'll let you know what happens ....

---

### Post by jenhsun on 2007-03-29
And please take a look at this site, it will help you build the site.
[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

During that time I was so lucky to have Mr C help me testing my router condition. You can focus on testing your router first or use the other router to link to the internet. Need to narrow down the problem, you know.:)

---

### Post by djearwig on 2007-03-29
I don't think the router is the problem.  I had php working just fine on the box; which is a LAMP server.  The problem started once I tried to install and configure LDAP.  Or maybe it was when I put Samba on the box and tried to get LDAP to read from Samba?  Or when I tried to virtualize with VMWare.  Doing to many things at once maybe.

Anyway, now that everything is up and running (expect the virtualization) I tried to test everything and so far, the only problem is the php.

I have done nothing with the router configuration...

---

### Post by jenhsun on 2007-03-29
> **djearwig said:**
> I don't think the router is the problem.  I had php working just fine on the box; which is a LAMP server.  The problem started once I tried to install and configure LDAP.  Or maybe it was when I put Samba on the box and tried to get LDAP to read from Samba?  Or when I tried to virtualize with VMWare.  Doing to many things at once maybe.

Anyway, now that everything is up and running (expect the virtualization) I tried to test everything and so far, the only problem is the php.

I have done nothing with the router configuration...

Hey, I am sorry that I know nothing about LDAP. But I found one info for you.
[http://tw2.php.net/ldap](http://tw2.php.net/ldap)
It's looked like    LDAP support in PHP is not enabled by default, I guess.
Anyway, sorry that I can't help that much.

---

### Post by djearwig on 2007-03-29
Don't worry about it.  I appreciate the help.

Thanks for the link.

---

### Post by djearwig on 2007-04-03
Anyone have any other thoughts on why php is not working on my server?

---

### Post by pppetter on 2007-04-03
Tip: Ask the same question in the Server & Security subforum(under "Other Support Categories") and you'll get help from server crazy people, that's the main place they look for people to help out with server stuff :)

---

### Post by djearwig on 2007-04-03
Thanks, I'll do that.

---

