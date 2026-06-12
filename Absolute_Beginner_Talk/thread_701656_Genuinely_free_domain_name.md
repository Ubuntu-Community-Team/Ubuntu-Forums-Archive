---
title: "Genuinely free domain name?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-02-19
I'm thinking about buying a new computer to install Ubuntu Server Edition on so I can host my own website.  I understand how most of the process works, but what about the domain name?  

Is there such a thing as a genuinely free domain name (.com, .net, .org)?  And if not, what in the world makes maintaining a paid one cost upwards of $7 average a month?!?

---

### Post by neurostu on 2008-02-19
No you can't get the domain for free. You have to buy a license from ICANN.  You can check with places like GoDaddy.com to see what the domain will cost.

Again you are just paying a licensing fee there really isn't any maintenance costs.

---

### Post by notwen on 2008-02-19
You can register a domain (ie. example.com) for under $10/year on avg, the hosting, which you would be doing on your server, would be what provides you w/ the monthly cost.
Check these registrars I prefer:
[GoDaddy]("http://www.godaddy.com")
[Dotster]("http://www.dotster.com/")

---

### Post by Niklas Schröder on 2008-02-19
Is there an alternative free domain like .co.nr that lets me have dns access?  I'm really poor and can't afford to buy a license year after year...

---

### Post by red_Marvin on 2008-02-19
If you do your own hosting you can use dyndns.org, they can provide names like youradressstuff.dyndns.org or somefittingname.homelinux.org and a couple of others

---

### Post by steveneddy on 2008-02-19
If you went to dyndns.com, you could have a website address like 

**yourname.dyndns.com**

and it will point to your machine.

Just have apache installed and a working web page and you are ready to go.

You will probably need to have an auto update client installed like

**[COLOR="Red"]ddclient[/COLOR]**

to make your server tell the servers at dyndns.com your IP address since you will probably have a dynamic (changing) IP address as opposed to a static (non-changing) IP address.

[COLOR="Blue"]Totally free, BTW.[/COLOR]

---

### Post by Niklas Schröder on 2008-02-19
From what I've seen, dyndns.org isn't free.  They have pricing details and everything.  I can deal with the dyndns.com extension, but I need to know how to get to it first...

---

### Post by Niklas Schröder on 2008-02-19
Ok.  I guess they are free.  Here's the page...

[https://www.dyndns.com/account/services/hosts/add.html](https://www.dyndns.com/account/services/hosts/add.html)

But how do I point it to my computer?  Just punch in the IP address?

---

### Post by dasunst3r on 2008-02-19
If you're going to get a domain name, for the love of God, DO NOT use Network Solutions.  They are the biggest rip off you will ever see.

---

### Post by Niklas Schröder on 2008-02-19
Then who would you suggest?  Like I said before, I'm dirt poor...

---

### Post by lespaul_rentals on 2008-02-19
> **dasunst3r said:**
> If you're going to get a domain name, for the love of God, DO NOT use Network Solutions.  They are the biggest rip off you will ever see.

+1

There is not such thing as a 100% free domain name.  There will always be some catch.  If you use a free one they may tack on a suffix (such as DynDNS does, <desiredname>.dyndns.org).  With others, the uptime will be horrible, and the name will only work 50% of the time.  Still other times -- and this may be the worst -- it will lead the end user through a chain of advertisements before reaching the destination.  Sometimes these are benign advertisements, other times spyware is involved.

You can get a domain name for very cheap.  I can lease one for 10 USD a year.

---

### Post by Niklas Schröder on 2008-02-19
:sigh:  Oh well.  I guess I'll just wait until I can find the money...

---

### Post by steveneddy on 2008-02-19
> **Niklas Schröder said:**
> Then who would you suggest?  Like I said before, I'm dirt poor...

I have used dyndns for a couple of years now and I never have to do anything to anything.

I wrote the web page.

I registered on dyndns.com web site.

I installed ddclient.

I set my Linksys router to auto update.

I am done.

Maybe an hour total, including installing the software.

ddclient is in the repos.

It is totally free. I have enjoyed the service and they have never let me down nor have they ever asked me for any money of bug me to upgrade.

---

### Post by Pandemic187 on 2008-02-19
Yes, DynDNS + Apache = free domain name. The tradeoff is that you can't get a .com, or even a .net. For a while I experimented running a website from my home box, which was accessed via the domain inzan3.ath.cx. DynDNS gives you options for different extensions, so I picked .ath.cx because it has the fewest characters.

But, more simply, you'll never get a .com for free.

---

