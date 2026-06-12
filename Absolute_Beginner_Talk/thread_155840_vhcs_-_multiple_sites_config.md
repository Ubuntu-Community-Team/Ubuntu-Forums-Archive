---
title: "vhcs - multiple sites config"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-04-05
Hey all,

I've looked through the wiki and "manuals" at vhcs and have been a little disappointed.

My question:  I want to setup a series of websites on my server.  How do I direct the nameservers to resolve to my server at the right folder?  Am I right in thinking I point a nameserver to:

myIPaddress.com/site1
myIPaddress.com/site2...

Does this sound right?

gs

---

### Post by spanishwasabi on 2006-04-07
Hi,

Lucky you, I'm still looking for the "manuals" :-P

I could not yet install vhcs, but here's how it works:

You have 1 server with Apache, and you have several domains:
a.com
b.com

or, if you prefer, several subdomains or folders:
c.a.com
a.com/web1

One thing is the DNS, that will resolve to the IP your server is on.
a.com/IP1
b.com/IP1
c.a.com/IP1
a.com/web1 is actually resolved to a.com

Then, the decision of which web site is asked for is handled by Apache with the different VirtualServers, that will know (due to the config file) which folder correspond to which domain or subdomain.

Hope its a bt clearer (if I did not misundertanded your question...).

Enjoy,

G

---

### Post by KingBahamut on 2006-04-07
[http://doc.gwos.org/index.php/VHCS](http://doc.gwos.org/index.php/VHCS) 

Hope this helps either of you.

---

### Post by guysmiley on 2006-04-10
Ok,

So as I understand it, I go to my DNS provider (i.e. namecheap.com) and direct all the urls I own to my IP.

Then, in Apache, I tweak the config file somehow...?  Does VHCS not do this for me already?

gs

---

### Post by spanishwasabi on 2006-04-10
Hi,

Yeah, that's the main idea. Usually those DNS providers give the option of a "catch all" address, something like *.yoursite.com that will redirect anything ending in yoursite.com to, well, your site :-)

As far as I understood, VHCS should allow you to do it automagically. That's the whole point of VHCS :-)

My main point on my last mail was: Don't mix DNS and HTTP server, they're two very distinct things.

Enjoy,

G

---

### Post by spanishwasabi on 2006-04-10
[QUOTE=KingBahamut][http://doc.gwos.org/index.php/VHCS](http://doc.gwos.org/index.php/VHCS) 

Hope this helps either of you.[/QUOTE]
Thanks.

I've actually tried this link, and I found some parts a bit confusing. Mainly I had to spend a bit of time to get that "silver part" difference ](*,) 

Well... I followed it, thanks a lot, and found that I still had problems with my initial error, that I already`posted in another thread.

Whatever... I'll keep trying :-)

G

---

### Post by guysmiley on 2006-04-10
Thanks too for the website howto.  I also found this somewhat confusing.

Just to clarify: does anyone know if VHCS automatically confgis apache for multiple domains on one IP?

gs

---

### Post by guysmiley on 2006-04-27
Alright,

I've done some more digging...  I have a VERY simple question now (before I begin transfering domains...!):

**[COLOR="Blue"]Do I instruct my nameservers to point domains to:[/COLOR]**

myIPaddress

[COLOR="Red"]or[/COLOR]
myIPaddress/site1/htdocs

[COLOR="red"]or[/COLOR]
myIPaddress/site1

?

Thanks in advance for your thoughtfulness,

gs

---

### Post by spanishwasabi on 2006-04-28
You must instruct your nameservers to point domains to:
myIPaddress

The rest (site1, site1/docs,...) is taken care of by Apache.

Enjoy!

G

---

### Post by guysmiley on 2006-04-28
Thanks, spanish!

---

### Post by guysmiley on 2006-04-28
PROBLEM!

When I go to my Domain Registrar and change my nameserver to myIPAddress, I get an error saying it's an invalid nameserver!!!

Help!

gs

---

