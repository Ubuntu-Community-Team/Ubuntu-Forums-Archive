---
title: "dynamic update client for 6.01 server"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-06-17
I just installed the turn key Ubuntu 6.06 LTS LAMP server.
I set up an account with [http://www.everydns.net/](http://www.everydns.net/) and have directed the DNS records to my registered url.  I then tried to run a pl script ([http://www.everydns.net/eDNS.pl](http://www.everydns.net/eDNS.pl)) and got this error:
```

Can't locate MIME/Base64.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./eDNS.pl line 38.
BEGIN failed--compilation aborted at ./eDNS.pl line 38.

```

Does the server include any kind of dynamic update client?  I have been Googleing about and attempted ddns, with no luck, I have tried to run apt-get to find a dynamic update client, but I can't seem to find anything... I am too new at this... 

I have used no-ip in the past on Fedora without any problems, but learned of everydns just recently and thought I would give it a go... but not much luck so far... please help!  
Thanks

---

### Post by mlind on 2006-06-17
You probably need libmime-perl package (which provides MIME/Base64.pm) ?
Or use cpan to retrieve the module, but I guess installing that library is better.

```

sudo aptitude install libmime-perl

```

What do you mean by 'dynamic update client?' cpan?

---

### Post by juicybananahead on 2006-06-17
Hmmmm. Maybe try ddclient. It's available in the universe repos.

---

### Post by kpm on 2006-06-18
[QUOTE=mlind]What do you mean by 'dynamic update client?' cpan?[/QUOTE]

It is a tool that allows those of us whose ISPs assign dynamic IPs to run a web server and have a DNS server resolve to our fully qualified domain name.

I did get the perl script to run after using apt-get to grab ddclient... ddclient does not have a default to everydns though, so I tried to configure it, but again, too new (and impatient) at this so went back to the script and it now runs.

Thanks!

---

### Post by kpm on 2006-06-18
[QUOTE=juicybananahead]Hmmmm. Maybe try ddclient. It's available in the universe repos.[/QUOTE]
 Thanks!  Grabbing ddclient seems to have installed the perl library I was missing as well, so now can run either!

---

