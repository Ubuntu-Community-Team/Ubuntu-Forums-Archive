---
title: "[SOLVED] &amp;quot;redirect&amp;quot; a domain to a specific ip"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2008-03-27
hello.
Ok here's the thing: a friend of mine bought 1 .ro domain 2 years ago and hosted the website somewhere he doesn't remember anymore since he hasn't updated it since last year... now he gave me full access to the domain (or at least he said so) and i want to "redirect" all the users when typing [www.thedomain.ro](www.thedomain.ro) to a specific ip.... the computer that owns that ip isnt a bought webserver, it is rather my second computer equiped with LAMP.

from what i've read by now seems that i have to modify the nameservers... now the problem is that even though i've documented myself alot i would say about what nameservers are, i can't understand where do i modify them and how do i modify them such a way that when typing [www.thedomain.ro](www.thedomain.ro) it goes to the ip i want to ?

thanx in advance...

---

### Post by hyper_ch on 2008-03-27
you normally set the nameserver at the place you registered the domain with. Nameservers point to an IP address that will actually host the zonefile for the domain.

The zonefile itself then contains the IP of where the domain is actually hosted at... you know, you can split up subdomains on different servers, have another server for the mail....

And then finally you need the webserver to listen to that domain (if you host multiple ones)...

Basically those three things must be set

(1) Nameserver entries to a dns server with the zonefiles

(2) DNS Server must set the actual ip of the domain in its zonefiles

(3) The actual server must contain valid entries for "displaying" a certain webpage when asked for the domain name.

Do you have a static IP address?

---

### Post by ahsile on 2008-03-27
You could use mod_rewrite with apache to redirect the browser to a new IP

```

RewriteEngine on

RewriteCond %{HTTP_HOST} ^http://(www\.)?some.domain.com
RewriteRule .* http://some.new.domain.com/$1 [R=301,L]


```

On the other hand, if you just want to change the domain record you need to figure out who the domain registrar is (use the whois database), and then you can contact them to make the change for you.

---

### Post by which_chick on 2008-03-27
In order to direct a domain to where you want it to go, you have to be authoritative for the domain.

The first thing to do is to pull the whois information on the domain.

[http://www.europeregistry.com/tools/whois.htm](http://www.europeregistry.com/tools/whois.htm)

Type in the domain name that you think you have.  DO not include any www stuff.  Just domain.ro is all you put in there.

If you get results that the domain name is not registered, then it isn't belonging to anyone.  If you do get results that the name is registered, then your results *may look something like this:

(These are results for google.ro, which is a handy example that we are using for illustrative purposes.)

```
domain-name: google.ro
description: Gervasoni Fabrizio
description: viale Zavaritt 234/E
description: 24020 - GORLE - BG - IT
description: phone: +39 035 4124408
description: fax: +39 035 4534078
admin-contact: DA170-ROTLD
technical-contact: DA170-ROTLD
zone-contact: DA170-ROTLD
billing-contact: DB758-ROTLD
[B]nameserver: NS1.GOOGLE.COM 216.239.32.10
nameserver: NS2.GOOGLE.COM 216.239.34.10
nameserver: NS3.GOOGLE.COM 216.239.36.10
nameserver: NS4.GOOGLE.COM 216.239.38.10
[/B]info: Register your .ro domain names at http://www.rotld.ro/
info: object maintained by ro.rnc local registry
notify: domain-admin@listserv.rnc.ro
object-maintained-by: ROTLD-MNT
mnt-lower: ROTLD-MNT
updated: domain-admin@listserv.rnc.ro 20000717
updated: danp@rnc.ro 20000717
updated: hostmaster-cmircea@rotld.ro 20020411
updated: danp@rnc.ro 20031127
updated: dan@rotld.ro 20060718
source: ROTLD
application-date: 20000519
domain-status: active
registration-date: 20000717

[B]person: DNS Admin
address: Google Inc.
address: 1600 Amphitheatre Parkway
address: Mountain View, CA 94043 US
address: US
phone: +16503300100
fax-no: +16506181499
e-mail: dns-admin@google.com
nic-hdl: DA170-ROTLD
object-maintained-by: ROTLD-MNT
updated: domain-admin@listserv.rnc.ro 20030505
source: ROTLD
[/B]
person: Domain Billing
address: 10400 Overland Rd.
address: PMB 155
address: Boise, ID 83709 US
phone: +1.2083895740
fax-no: +1.2083895799
e-mail: ccops@markmonitor.com
nic-hdl: DB758-ROTLD
info: object maintained by ro.rnc local registry
notify: domain-admin@listserv.rnc.ro
object-maintained-by: ROTLD-MNT
updated: dan@rotld.ro 20060718
source: ROTLD


```

What you want to look for is the stuff that I have bolded in the example. 

1.  Are there authoritative name servers?  (A nameserver answers the call for "What IP addres is www.blah.ro?"  An "authoritative" nameserver for google.ro has the absolute right to answer that question because it is owned/administered/hired by google to answer the question properly.  For you to be able to "redirect a domain to a single IP", you need to BE or have the ability to CONTROL the authoritative name servers for the domain.)  Usually, the authoritative name servers are provided by (a) your registrar or (b) your hosting company though there is nothing to prevent you from being your own authoritative nameserver (as long as you have a static IP address and a permanently-up internet connection).

2.  Who is the administrative and/or DNS contact for the domain?  (The administrative and DNS contacts are the people who get to say what the authoritative nameservers for the domain are.  They are the people who, in effect, "own" the domain name.)

This should get you started.

---

### Post by which_chick on 2008-03-27
Assuming that you *are* the Admin/DNS contact on the domain name, that you know where your registrar is (I only have experience with Network Solutions and they don't handle .ro domains), and that you know how to admin your domain name (usually this will be a log-in-on-the-website kind of thing), then all you need to do is to update the nameserver information on file with the registrar so that your domain name and its authoritative nameservers will show up in the root servers.  Then, you go to your nameservers (that you just told the registrar about) and you tell them where you want [www.yourdomain.ro](www.yourdomain.ro) to go.  

If there are already authoritative nameservers listed for your domain, removing the (example) ns1 from ns1.hostingcompany.com and putting in [www.hostingcompany.com](www.hostingcompany.com) will frequently give you their website.  If these exist, they are probably the hosting company where your friend had the thing hosted.  They might even have an email for tech support, that kind of stuff.  

Here's a little more information on how DNS works:

DNS is a hierarchy.  

There are top level servers (a.root-servers.net, b.root-servers.net, etc.)  There are secondary servers (a.gtld blah blah -- it's been a while since I needed this stuff).  These high-level servers are run by registrar-like entities such as networksolutions.com.  The top level servers hold the lists of domains and the information about which servers are authoritative for which domains.

The top-level servers do not resolve hosts.  They tell other DNS servers *where to go* to resolve hosts.

In real life, when Joe User wants to see [www.google.com](www.google.com), he types that into his browser. 

His computer sends the stuff to his DNS server (usually provided by his ISP). 

 "His" DNS server looks in its local cache (to see if it already has an entry for google) and, if not, it asks the root servers where to go for *authoritative* google.com information.

The root servers say that authoritative google.com information can be had from any of the following:  NS3.GOOGLE.COM    NS4.GOOGLE.COM	 NS1.GOOGLE.COM  NS2.GOOGLE.COM	

Joe User's DNS server THEN goes to one of the four google.com DNS servers and asks for where, precisely, is the IP address of [www.google.com](www.google.com) at the moment.  Google's authoritative servers reply and then the DNS passes that information (the IP address) back to Joe User's computer and Joe User gets his page.  Yay!

In fewer words:

User sends query to local DNS. 

Local DNS sends query "Where is authoritative information about X.com?" to root servers.  

Root servers say "Authoritative information about X.com is at ns.X.com"

Local DNS sends query "Where is www.X.com" to ns.X.com

Ns.X.com says "It's at 206.99.145.2" (or whatever)

Local DNS returns that information to user's computer, page resolves, joy is widespread.

---

### Post by the_nomad on 2008-03-27
first of all thank you for replying :)

ok so you're saying that i should be able somewhere to:
- change the nameserver responsbile for translating [www.thedomain.ro](www.thedomain.ro) -> the ip address
- change the ip address where [www.thedomain.ro](www.thedomain.ro) "points" to
right?

the nameservers of that domain are ns1.awardspace.com, ns2.awardspace.com etc. so in the control pannel at [www.awardspace.com](www.awardspace.com) i should be able somewhere to change the ip address to which [www.thedomain.ro](www.thedomain.ro) points to?

im kinda confused with where and what i am able to modify things...

i saw on some domain registering companies that they also offer hosting and i think that administrating these 2 (domain and hosting) isnt big deal... but what happens if i only buy the domain and i want to "point" that domain to a specific ip address? im sooooooo confused :(

LE: by the way... i now understand what [this]("https://www.dyndns.com/support/kb/what_is_dns.html") supposed to explain :D

---

### Post by which_chick on 2008-03-27
> ok so you're saying that i should be able somewhere to:
- change the nameserver responsbile for translating [www.thedomain.ro](www.thedomain.ro) -> the ip address


Correct.  This is done with the registrar, by changing the "authoritative server" to a nameserver that you run/control.  This would be the proper step to do if you want to set up and run your OWN nameserver.  

If it were me, I'd see what I could do using the pre-made and functional nameservers at awardspace.com first, though.  It'd be easier -- trying to bootstrap all of this at once when you're confused with it is a bit much to put on your plate at one go.

> - change the ip address where [www.thedomain.ro](www.thedomain.ro) "points" to
right?


Correct.  This is done INSIDE the "authoritative server", which currently looks like ns1.awardspace.com.

> the nameservers of that domain are ns1.awardspace.com, ns2.awardspace.com etc. so in the control pannel at [www.awardspace.com](www.awardspace.com) i should be able somewhere to change the ip address to which [www.thedomain.ro](www.thedomain.ro) points to?


Exactly.  Yes.  If you have a control panel (and a username and password and stuff) at [www.awardspace.com](www.awardspace.com), you should be able to set up name resolution for various hosts at thedomain.ro, including www.

> im kinda confused with where and what i am able to modify things...


Some confusion is normal.  DNS becomes more clear when you've messed with it for a while.

> i saw on some domain registering companies that they also offer hosting and i think that administrating these 2 (domain and hosting) isnt big deal... but what happens if i only buy the domain and i want to "point" that domain to a specific ip address? im sooooooo confused


If you buy the domain and want to "point" that domain to a specific ip address, you have to set up the authoritative DNS servers with the registrar.  You can (quite probably) just buy DNS from the hosting company.  Set up the DNS with how you want the host (or hosts) to resolve.

[www.thedomain.ro](www.thedomain.ro) is A HOST on the DOMAIN thedomain.ro.  When you do a nameserver file, you can choose to make many hosts (pop3.thedomain.ro, smtp.thedomain.ro, radius.thedomain.ro, ftp.thedomain.ro) or just one.  It's all up to you.

---

### Post by the_nomad on 2008-03-30
thanx alot :)

---

