---
title: "connectiong to wifi hotspots"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by zagu on 2007-02-04
Hello all,
I've been migrating to ubuntu for about a month now.  as it turns out, I'm going to traveling all over the US for a few months and will need to access the internet at various locations.  Is there any way to make my connections secure/encrypted in Linux.  I know there is something called jiwire or perhaps AnchorFree for windoze.  Does anyone have an idea of how I can secure my internet traffic if I don't have a base server anywhere to set up vpn?

thanks in advance

---

### Post by Paerez on 2007-02-04
The thing with security is that when communicating from point A to point B, both ends must be secure.

Lets consider your setup at a coffeeshop:
A = you
U = coffeeshop unsecured router
B = the site you are accessing

It goes:
A -> U -> B
Which is unsecure all the way, because B is not secure, even if A wants to be.

Using a secure VPN to your server S it goes:
A -> U -> S -> B

Now, A to S is secure because both A and S support the security. Then S forwards your traffic unsecurely to B, since B doesn't support security. But since you have S, it is secure from A to S and thus people at U can't read your traffic.

So you need to find a middleman S who is willing to share his bandwidth with you to make it secure.



I hope that gives you more info to help you and others find a solution.

---

### Post by zagu on 2007-02-05
jeez, thanks.  I was pretty sure there wasn't a VPN service like that.  

oh well.  

thanks for the reply.

---

