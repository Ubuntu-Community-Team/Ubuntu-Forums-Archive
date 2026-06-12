---
title: "Things to know after installing DNS server?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by strider* on 2008-01-16
i had install DNS server in ubuntu.. now what should be the things i should do next or to configure? please  help me guys..

---

### Post by zvacet on 2008-01-16
Read [this](http://doc.ubuntu.com/ubuntu/serverguide/C/).

---

### Post by hyper_ch on 2008-01-16
what do you want to do with it?

---

### Post by zipperback on 2008-01-16
> **strider* said:**
> i had install DNS server in ubuntu.. now what should be the things i should do next or to configure? please  help me guys..


Please clarify what you plan on doing with it. If you plan on hosting domains then you will need at least two dns servers, so you will need to either setup a second machine or have someone else run secondary dns for you.

- zipperback
:popcorn:

---

### Post by hyper_ch on 2008-01-16
> **zipperback said:**
> If you plan on hosting domains then you will need at least two dns servers

That's not quite true :)

Depending on the registrar you can operate "two" nameservers pointing to the same IP address. Other registrar demand different IP addresses. Those "two" nameservers can also be the same by listening to different domains or having different IPs associated to them.

---

### Post by zipperback on 2008-01-16
> **hyper_ch said:**
> That's not quite true :)

Depending on the registrar you can operate "two" nameservers pointing to the same IP address. Other registrar demand different IP addresses. Those "two" nameservers can also be the same by listening to different domains or having different IPs associated to them.


You can operate two different virtual dns servers on the same physical box using two different ip addresses, however in order to ensure proper operation of your network you should really have two different physical dns servers.

-zipperback
:popcorn:

---

### Post by hyper_ch on 2008-01-17
> **zipperback said:**
> however in order to ensure proper operation of your network you should really have two different physical dns servers.
You don't even need to different IPs... some domain registrars allow it just with two different ns-domain names to one ip address...

And if you host everything on one machine how would a second dns server ensure proper operation if the the main machine fails anway...

---

### Post by zipperback on 2008-01-17
> **hyper_ch said:**
> You don't even need to different IPs... some domain registrars allow it just with two different ns-domain names to one ip address...

And if you host everything on one machine how would a second dns server ensure proper operation if the the main machine fails anway...



For the typical home user who just wants to run a domain or two on a single box, you are correct, it would probably be fine.

It really all comes down to how comfortable a person is with the understanding that there isn't going to be any redundancy, and that it all comes down to a single point of failure.

- zipperback
:popcorn:

---

### Post by HydenPLainsite on 2008-01-18
Found this thread...

I was originally going to post, "What do I need to install DNS for?" From reading this post it looks like I need it to host a (or multiple) website(s) on the server.

I could use another servers dns though couldn't I? I think if the resources are available that would probably be ideal.

But if I don't have another one to use, I need to install it on the one server I have in order to serve the sites host. 

Are my assumptions correct? I'm just trying to figure out if I need to install DNS or not and it sounds like I do.

You help is greatly appreciated! Hope you don't mind the newbie post.
Hyden

---

### Post by hyper_ch on 2008-01-18
you could also host your own caching dns servers... so that one will be queried for domaine name resolution and not your provider's one... that "could" increase speed for cached domains...

---

### Post by dcstar on 2008-01-18
> **HydenPLainsite said:**
> Found this thread...

I was originally going to post, "What do I need to install DNS for?" From reading this post it looks like I need it to host a (or multiple) website(s) on the server.
.......

You do not need a DNS server on the Internet unless YOU own a Domain Name and YOU want to host/control the entry on your own server.

There are a multitude of DNS hosting services available on the Internet, and unless you are intending to set up web hosting (or whatever) 24/7 then there is little need for you to set one up.

If you just want it for your internal network then you can set one up, but it seems a lot of trouble for such an application.

---

### Post by HydenPLainsite on 2008-01-18
Thank you hyper_ch and David. I installed DNS so I could learn more.
Hyden

---

