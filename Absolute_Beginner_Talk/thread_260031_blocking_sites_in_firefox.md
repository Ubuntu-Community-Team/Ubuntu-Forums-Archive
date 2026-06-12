---
title: "blocking sites in firefox"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by rackne on 2006-09-18
i was wondering if it's possible to block some websites in firefox. i mean, if there's a group of users on a computer and an administrator doesnt want them to view certain websites is there's a way to lock those pages?

---

### Post by kidders on 2006-09-18
Hi there,

The web browser is the wrong thing to focus on ... after all, your users could simply switch to another one! What you need is a www proxy like squid.

---

### Post by rackne on 2006-09-18
where can i get it from? are there any other tools that could help to block given sites in a browser?

---

### Post by rackne on 2006-09-18
never mind i found it. but anyways are there any other applications, preferably with GUI?

---

### Post by kidders on 2006-09-18
Squid is available from Ubuntu's package repository.

There are other possibilities, but squid is the smartest choice by a long way imho. What you would do is:

[LIST=1]
[*]Proxy all web traffic.
[*]Log proxied requests for your own interest.
[*]Optionally install an extension to squid to give you *very* fine-grained control over what people can access, if squid's own features aren't enough for you.
[*]Set up proxy authentication to help you identify individual users, or use fixed DHCP address assignments to identify individual computers, so you can start being "smart" about what gets blocked.
[*]Consider transparent proxying/authentication schemes, so your users don't even realise their web traffic is being intercepted.
[/LIST]

Of course, proxying per se often increases performance, so if your internet connection is being shared, you should probably consider using squid anyway!

Hope this helps :-)

---

### Post by rackne on 2006-09-18
that helped a lot, man. thanks!

---

### Post by kidders on 2006-09-18
No problem :-)

I suggest you take things a step at a time though ... don't try to go the whole hog in one go! Specifically, you should leave the transparent proxying 'til the end.

**One quick point I forgot about:** Microsoft proxy servers can use NTLM to authenticate windows boxes transparently ... in other words, a proxy user can be made to log into the proxy without realising it, which is totally daft, but very convenient. If you have Windows boxes on your network, you will have considerable difficulty replicating this style of proxying with squid, though :-(

---

### Post by tomBorgia on 2006-09-18
Hold on m8... you just need to redirect to localhost from the /etc/hosts file/

Simply add the following to your hosts file -

127.0.0.1 [www.thewebsiteiwantoblock.com](www.thewebsiteiwantoblock.com)

and any requests to that site will redirect locally...

You'll need to make sure your users can't edit the hosts file!

---

### Post by kidders on 2006-09-18
Yep :-) That'll work fine if:

[LIST=1]
[*]You don't mind blocking entire domains.
[*]You know where everything you want to block is hosted in advance.
[*]Your PC is managing DNS for your entire network.
[/LIST]

It's certainly **a lot** easier ... just not as flexible.

---

### Post by tomBorgia on 2006-09-18
Fair doos... :D

---

### Post by bodhi.zazen on 2006-09-18
[How to use Hosts via an automated script](http://ubuntuforums.org/showthread.php?t=241460#2)

Works well, up to date.

---

