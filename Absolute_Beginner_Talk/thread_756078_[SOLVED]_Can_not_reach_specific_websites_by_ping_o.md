---
title: "[SOLVED] Can not reach specific websites by ping or browser"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by dominicw on 2008-04-15
I can see most websites however I have a couple that load fine on my other computers but not my Ubuntu install.  I can not even ping them, whereas I can ping and view other sites just fine.

Two of the websites I can not access through browser or ping are:

[www.cnr.com](www.cnr.com)
[http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)


Any thoughts on what might stop me from getting to a couple of specific sites like this?

Dominic

---

### Post by Xiong Chiamiov on 2008-04-15
I'm on Windows right now, and I can't access either of those.  Probably you have a cached version of them on your others computers that shows how they were last time you viewed them.

---

### Post by dominicw on 2008-04-15
I just used my wife's computer to look at those sites and loaded [www.cnr.com](www.cnr.com) fine.  Her computer never has been to that website.

Any thoughts?

Dominic

---

### Post by dominicw on 2008-04-15
I just tested about a dozen more sites on the Ubuntu laptop, ones that I have never been to on that machine.  All loaded except for openoffice.org which I am able to get to on 2 other computers.

I do not believe cache is an issue....

Dominic

---

### Post by michaeld003 on 2008-04-15
Try pinging the ip addresses of those sites to see if it is a DNS issue.

86.110.224.72 and 198.172.200.26

If they go through then it is probably a DNS issue.

---

### Post by Delkster on 2008-04-15
Cnr.com doesn't seem to respond to ping (not all sites do), but the website loads okay albeit after a small delay.

---

### Post by dominicw on 2008-04-15
> **michaeld003 said:**
> Try pinging the ip addresses of those sites to see if it is a DNS issue.

86.110.224.72 and 198.172.200.26

If they go through then it is probably a DNS issue.

I am unable to ping either the domain name or the ip address.  I also tried openoffice.org for both domain and ip to no avail.

I tried some other websites and their associated IPs such as one of my websites and google and both pinged fine.

So far this is what I know:

I can reach and ping these sites on other computers here at my house.  I can not reach them via my Ubuntu laptop either from browser or ping (both domain name and IP)

I can reach other sites that I have tried via the Ubuntu machine, including ones that I have never visited (just random testing)

Dominic

---

### Post by Sidewinder1 on 2008-04-15
I just connected to 'cnr' and 'kanz' using ubuntu / Firefox with no problems; as an aside I had all scripts blocked and both sites came up fine so it's not a blocked scripts issue. Don't feel too bad, this has me stumped too; if it 'touches' one site it should do all..??..

---

### Post by dominicw on 2008-04-15
> **Sidewinder1 said:**
> I just connected to 'cnr' and 'kanz' using ubuntu / Firefox with no problems; as an aside I had all scripts blocked and both sites came up fine so it's not a blocked scripts issue. Don't feel too bad, this has me stumped too; if it 'touches' one site it should do all..??..

Just for fun, I decided to try those website from a live cd session....they all loaded fine.

I went back and booted back into my install and they are not coming up......

Is there something that would be blocking these that I am missing?

Dominic

---

### Post by dominicw on 2008-04-15
It is now working after an additional reboot...I will try to see if anything in particular happens that I can post here to help others that may run into this problem.

Thanks for the input!

Dominic

---

