---
title: "Dos Protection?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by useLinux, on 2007-04-27
I'm thinking of maybe running a very basic version of a server using either my pc, (testing server with some users etc) or using another basic machine. Like an older machine, with an AMD 1400+ processor or something. Nothing great. But alot of people are talking about DoS attacks, and how it would really mess me up. Which i know. 
Do you know any programs that could help me get like Anti DDoS protection etc. (Freebi's Mostly) but if i must pay then i would think about it. I DONT want to know what DoS attacks are, i already know! I want to know, how to protect them. Thanks if you help.

---

### Post by LaRoza on 2007-04-27
Here's an article that may be helpful. I am sorry I can't explicitly answer your question.

[http://www.gcn.com/print/vol20_no17/4573-1.html?topic=news](http://www.gcn.com/print/vol20_no17/4573-1.html?topic=news)

---

### Post by useLinux, on 2007-04-27
> **LaRoza said:**
> Here's an article that may be helpful. I am sorry I can't explicitly answer your question.

[http://www.gcn.com/print/vol20_no17/4573-1.html?topic=news](http://www.gcn.com/print/vol20_no17/4573-1.html?topic=news)

It doesnt actually tell you how to properly defend yourself though.

---

### Post by Cypher on 2007-04-27
To properly protect yourself from a DoS attack you should first and foremost employ a hardware firewall. You can also enable a software firewall within Ubuntu for futher protection. But it's better to do it with hardware..

---

### Post by useLinux, on 2007-04-27
> **Cypher said:**
> To properly protect yourself from a DoS attack you should first and foremost employ a hardware firewall. You can also enable a software firewall within Ubuntu for futher protection. But it's better to do it with hardware..

Thanks, any idea where i can get one? Order 1 etc that is reliable. I dont trust most online shops etc. :P

---

### Post by Cypher on 2007-04-27
Any recent router will also include a firewall. I use a Linksys WRT54GS wireless broadband router that works really well.

---

### Post by nixclusive on 2007-04-27
Theoritically, (D)DoS attacks are best avoided at their very origin i.e. at the originating machines own service providers. But hey, *Theoritically* generally translates to *doesn't really happens that way* ;-)

You can however set up a throttling server to requests the legitimate incoming taraffic to slow down based on the current network condition. Or maybe use the [TARPIT](http://www.securityfocus.com/infocus/1723) target in the linux kernel netfilter.

---

### Post by useLinux, on 2007-04-29
> **Cypher said:**
> Any recent router will also include a firewall. I use a Linksys WRT54GS wireless broadband router that works really well.

I have that exact router. :) Did you have to config the settings in its cpanel? Or it just works fine as it is?

---

